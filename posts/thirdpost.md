---
title: Web Development Docker
date: 2020-01-01
author: Jane Doe
summary: Why contemplating our mortality can be a powerful catalyst for change
tags:
  - tech
  - politics
---
Docker, the leader of the industry for developing and maintaining websites. Docker is extremely powerful because it allows developers to package applications into containers. This has many benefits including saving time, money, and allowing for scalability. It allows allows for developers to test applications in its own "Container" in a timely manner.

## How To Get Started With Docker
Honestly before 2 weeks ago, I had no idea what Docker was. I learned lot with how and why it works once I started to get hands on with docker. But before we get into that I wanted to address what docker needs in order to run your application.

#### DockerFile
The docker file is the most crucial part needed to set up an application in docker. Here is an example of a simple docker-file for the newsAPI micro service that I can post how to setup in docker towards the end of this post.
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/j2cbghr3izng44bcca8q.png)
Basically what this "DockerFile" does is that is automates all the code and commands needed to setup the application on a new device(In this case the new device is the new docker instance.)

###### How to create a DockerFile within the Docker Playground
Step One: Add a new instance into your docker playground

Step Two: Clone the necessary project from GitHub Example: `get clone "GitHub Link here"` Note: Do not use parenthesis in your code for this step

Step Three: Create your Docker file by using: `touch DockerFile` 

Step Four: You can now use the editor to insert the necessary code into your DockerFile (Use the screenshot above to help you setup the correct commands needed into your docker file.) Note: Some Applications will need more steps within the file to get it to run within docker.

### newsAPI Micro service Fully setup
Here are some screen shots to show what the end result looks like once you are able to get the newsAPI Micro Service setup.
Screenshot 1(the end result):
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/82zk10au1b7mmc36tmp8.png)
Screenshot 2(Manually searching through the API data base for tesla info):
![Image description](https://dev-to-uploads.s3.amazonaws.com/uploads/articles/439q85p997fwk4aomtbu.png)

## Links to get started with Docker
#### Link 1 
[Docker 101 Tutorial](https://www.docker.com/101-tutorial)
#### Link 2
[Walkthrough Setting up newsAPI microService with Docker](https://github.com/heyMP/ist402-docker/tree/master/labs/7-news-api-microservice)
