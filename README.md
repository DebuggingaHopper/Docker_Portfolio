
# What will we work on?

1. [Create a Web server on Nginx through a docker container]([Building a Web Server using Docker: A Beginner’s Guide to DevOps | by Yasholo | Medium](https://medium.com/@Yasholo/building-a-web-server-using-docker-a-beginners-guide-to-devops-edf1df75f33a#:~:text=Step-by-Step%20Guide%201%20Step%201%3A%20Install%20Docker%20Before,Step%208%3A%20Monitor%20and%20Troubleshoot%20...%20More%20items))
Within this project we will be able to get a better breakdown of applying this in an actual project

In this project we will be using the provided docker file
```docker
FROM nginx:alpine  
COPY index.html /usr/share/nginx/html/  
EXPOSE 80  
CMD ["nginx", "-g", "daemon off;"]
```
- `**FROM nginx:alpine**`**:** We’re using the lightweight `alpine` version of Nginx as our base image.
- `**COPY index.html /usr/share/nginx/html/**`**:** This command copies our `index.html` file into the Nginx default directory inside the container.
- `**EXPOSE 80**`**:** This exposes port 80, allowing traffic to reach our web server.
- `**CMD ["nginx", "-g", "daemon off;"]**`**:** This command runs Nginx in the foreground, ensuring that the container remains active.

This is where this [documentation for building docker images](https://www.bing.com/search?q=file+extension+for+docker+image&qs=n&form=QBRE&sp=-1&ghc=1&lq=0&pq=file+extension+for+docker+image&sc=8-31&sk=&cvid=A0169B6A55BB415ABD1AC69B0758C5FA&ghsh=0&ghacc=0&ghpl=)comes in handy:

The current directory for this project is C:\Users\nelso\webserver-docker
![[Pasted image 20240907232030.png]]
To access this we can get to it thrpugh [Docker Web Server](http://localhost:8080/)

This has now allowed us to get a step closer to our goal. As this is us learning about devops this [simialr tutorial]([Building a Web Server using Docker: A Beginner’s Guide to DevOps | by Yasholo | Medium](https://medium.com/@Yasholo/building-a-web-server-using-docker-a-beginners-guide-to-devops-edf1df75f33a#:~:text=Step-by-Step%20Guide%201%20Step%201%3A%20Install%20Docker%20Before,Step%208%3A%20Monitor%20and%20Troubleshoot%20...%20More%20items)) gives extra steps of what to look at

We can now break even more what we did, we created an image called webserver-docker. so ideally when we create images we do not want to do it without some tags / version defining to ensure we do not have a bunch of random images that have no specefications of what they are.

So let's destroy our old container and image

now lets follow this [guide]([How To Build Docker Image [Comprehensive Beginners Guide] (devopscube.com)](https://devopscube.com/build-docker-image/#:~:text=docker%20build%20-t%20nginx%3A1.0%20.%201%20-t%20is,docker%20build%20context.%20That%20is%20our%20current%20directory.)), to ensure we create the image more effeciently so thar way we are following best parctices.

sO what I did was change my docker file to the following:
```
FROM nginx:alpine
COPY ./html /usr/share/nginx/html/
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
![[Pasted image 20240908160833.png]]
```
docker run -d -p 8080:80 --name my-webserver webserver-docker:1.0
```


Now what I did was change my image to include the portoflio page on his nginx web server I have created, so I had to make a few changes in my image folder as you see