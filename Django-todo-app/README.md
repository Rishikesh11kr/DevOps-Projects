
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

Cheers and Happy Coding :)

