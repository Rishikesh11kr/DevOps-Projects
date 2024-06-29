
# Django Todo App


This is a simple Todo application built with Django and deployed using Docker, Jenkins, and Amazon EC2.


GitHub ---->Docker----->Jenkins------> Amazon (EC2)
## Deployment

Step 1 : Clone the project form github or any source to run and deploy 

```bash
  git clone "github link"
```
now we have to install django
```
pip install django
```

Once you have downloaded django, go to the cloned repo directory and run the following command

```bash
python manage.py makemigrations
```

This will create all the migrations file (database migrations) required to run this App.

Now, to apply this migrations run the following command
```bash
python manage.py migrate
```

One last step and then our todo App will be live. We need to create an admin user to run this App. On the terminal, type the following command and provide username, password and email for the admin user
```bash
python manage.py createsuperuser
```

That was pretty simple, right? Now let's make the App live. We just need to start the server now and then we can start using our simple todo App. Start the server by following command

```bash
python manage.py runserver
```

Once the server is hosted, head over to http://127.0.0.1:8000/todos for the App.

Successfully created virtual machine to run todo app:-

![image](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/30229dc3-49cb-4362-b8a2-46760e8e8fd3)


----------------------------------------------------------------------------------------
connecting with Amazon EC2
![image](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/833314d0-8c09-4e84-908a-e79eaffdb24c)

Copy SSH link and open the terminal where your "pem file " is downloaded and past the link -
![Screenshot 2024-06-14 134256](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/043418ad-40c6-4fa8-af06-40c6d67e1a24)

# Deploying the project on docker
* Step 1) follow all above process and run the command 
* Step 2) Install Docker in your system 
```
sudo apt install docker.io
```
* Step 3) Now writing commands for docker( eg: develop image container of Django)
```
vi Dockerfile
```
* Step 4) Now write all commands for Container image
```
FROM python:3
RUN pip install django==3.2
COPY . .   #first dot is for source and second is for Destination
RUN python manage.py migrate
CMD ["pyton","manage.py","runserver", "0.0.0.0:8001"]

```
![Docker commands ](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/3366cce8-41d4-4e5a-b834-0ad849ae2291)

* Step 5) Successfully created Docker file.
* Step 6) Now creating the image from Docker file
```
sudo docker build . -t todo-app
```
Step 7) run the docker image: *"sudo docker run -p 8001:8001 dockerid"*
Step 8) Successfully, Deployed the project on Docker

***********************************************************************************************************
# Deploying the project on EC2 :star_struck:


```
vi todoApp/settings.py
```
To change Server and Time Zone
![image](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/d3cd3747-d8fc-4873-bce2-56ec11798bf1)

![image](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/c523b850-966b-4773-91e0-a19f74072c3d)



by By clicking on security of EC2 we can allow port private port to local port,
EC2> Security Groups >Edit inbound rules> add Custom TCP(8000/8001) > save rules



```
0.0.0.0:8001
```
![image](https://github.com/Rishikesh11kr/DevOps-Projects/assets/90023335/9d3a0588-732a-4d70-b771-f8bb78110baa)

Cheers and Happy Coding :)

