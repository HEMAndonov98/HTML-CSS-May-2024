---
layout: post
title: "Running Code using Docker"
description: Showing how to run a basic webpage using Dokcer
date: 2024-11-29 15:20:00 +0300
categories: updates
author: Hristo
background: https://images.unsplash.com/photo-1646627927863-19874c27316b?q=80&w=3280&auto=format&fit=crop&ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8fA%3D%3D
---

# Welcome to the world of containers

## What is Docker

Docker is a platform that allows us devs to focus on the code not the setup, Docker handles all the boring tasks like downloading the correct libraries and dependencies in order to run our code and packages them in a neat container that can be run and just works!

But how do we get started with docker?

### Getting Started

#### Homebrew

If you are using a Mac and Homebrew the easiest way to get started using Docker is by simply running.

```shell
brew install --cask docker
```

This will intall the needed software in order to use docker and also includes a cool GUI(in this demo we will only be using the docker CLI)

#### Regular Insrallation

-   Got to the [Docker Website getting started page](https://www.docker.com/get-started/)
-   Download and install the Docker desktop app
-   Start conteinerasing :)

#### Linux Server Intallation

First make sure your flavour and version of Linux is compatible with Docker, check the [Docker Documentation](https://docs.docker.com/engine/install/)
As of 29-11-2024 these are the OS requirements for Ubuntu

-   Ubuntu Oracular 24.10
-   Ubuntu Noble 24.04 (LTS)
-   Ubuntu Jammy 22.04 (LTS)
-   Ubuntu Focal 20.04 (LTS)

Use the convenience script to install everything automatically

```shell
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

### Create a simple web app

If you want you can create your own app that you can create a docker iamge from or just copy the code from my simple web app which is just a Hello world text centered that when clicked changes the background color of the web page.

#### Code

##### HTML

```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta name="viewport" content="width=device-width, initial-scale=1.0" />
		<script src="scripts.js"></script>
		<title>Test Container</title>
	</head>

	<body
		onclick="changeBackground()"
		style="height: 100vh; display: flex; flex-direction: column; justify-content: center;">
		<h1 style="text-align: center;">Hello World</h1>
	</body>
</html>
```

##### JavaScript

```js
function changeBackground() {
	const body = document.body;
	const colors = ["yellow", "red", "green", "purple"];

	body.style.backgroundColor = colors.random();
}

Array.prototype.random = function () {
	return this[Math.floor(Math.random() * this.length)];
};
```

##### Dockerfile

We will create a Dockerfile file in our root directory and paste this code instde it.

What this dose is tell Docker to create a image that will use nginx (a lightweight web server) then copy all the files in our root to the /use/share/nginx/html directory, then expose port 80(the default nginx port) and in the end run nginx

```
FROM nginx
COPY . /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```

#### Creating our first image

We then need to open a terminal window in our root directory of our web app and paste this command

```shell
docker build -t test-webapp-nginx .
```

this will create a test webapp nginx image from our Dockerfile

#### Running our first container

The final step is to run this code

```shell
 docker run --name test-nginx -d -p 8080:80 test-webapp-nginx
```

which will do these things:

-   run a docker container
-   --name: name the contaienr test-nginx
-   -d detach the container(This is so that it will not close after running)
-   -p create a bride from prot 8080 to port 80 so that when we go to localhost:8080 we will be routed to host-ip:80
-   the final argument is the name of our docker image

### Congradulations

You've successfuly packaged your first web app and run it as a container using Docker now you can go to (https://localhost:8080) and see your web app running.

This is the first step in the world of Docker and contaieners and shows just how powerful a tool like Docker can be to us developers, happy coding devs...
