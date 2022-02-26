---
title: How We find the IP address and use it to find Longitude and Latitude
summary: Using ipaddress to expand
date: 2022-02-25
author: Brian
tags:
  - beginners
---
**Brt5181**

## IP FAST API (Finding IP)
To start of I wanted to introduce how we get the IP address by using the [IP Fast API](https://ip-fast.com/api/ip/?format=json&location=True). If you click on this link and open it in a new tab it should display all of the raw data that the api can output. This api is how we can find the IP Address show below.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/fbb2wfgy0r7rq4mic4yi.png)
In the UpdateUserIP() function, The method will fetch the ipLookUp which is the API link displayed above, then will check to see if it can be processed with this statement here: 
`
return fetch(this.ipLookUp)
      .then(resp => {
        if (resp.ok) {
          return resp.json();
        }
        return false;
      })
`
After this method verifies that we can use the json data. We then move to where we will pick apart the data so that we can use it to display and use with the the GeoIP that we will discuss later. Here is where we can convert specific parts of the json into variable: 
```
.then(data => {
        this.ip = data.ip;

        this.location = `${data.city} ${data.country}`;
        return data;
      });
```
Now that we have the IP address stored as "this.ip" we can now tag the ip address as UserIP. Honestly I still don't completely understand the Tag process but I do know that it has something to do with the Lit Dependency.

We now have access to the provided IP address which now means we can use our IP Address with the next API in order to find out the Latitude and Longitude. The API we used to do this is: [FreegeoIP](https://freegeoip.app/json/). Again if you're interested to see how the data is portrayed with this API, Just click on the link and you should be able to see the array of data.

## GeoIP API

Below will be the method that allows us to create a new element of the userIP class that we can use for the "Freegeoip" API in order to determine the Longitude and Latitude.

## Combination of both API's

```
async getGEOIPData() {
    const IPClass = new UserIP();
    const userIPData = await IPClass.updateUserIP();
    return fetch(this.locationEndpoint + userIPData.ip)
      .then(resp => {
        if (resp.ok) {
          return resp.json();
        }
        return false;
      })
      .then(data => {
        console.log(data);
        this.lat = data.latitude;
        this.long = data.longitude;
        this.city = data.city;
        this.state = data.region_name;
        return data;
      });
  }
```
As you can see in the method above, It will fetch the location endpoint which is the "FreeGeoIP" API and the User IP that was pulled from the "IP fast" API. The process again check to validate the JSON, then we can pull the data (latitude, longitude, city, and region_name) into their own variables.

## GITHUB LINK TO PROJECT
Here is A link to our Groups Project: [IST402 Git Project](https://github.com/IST402GroupB/ip-project.git) The code/Topics I discussed will be located in the source folder under "UserIP.js" (IP Fast API) and the "LocationFromIP.js" (Free Geo IP as well as the combination of the two)
If your interested in running the project, Take a look at "Intro to front end" Blog that will show you the tools necessary for you to run this GitHub project.
