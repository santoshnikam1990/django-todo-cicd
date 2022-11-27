# django-todo
A simple todo app built with django

![todo App](https://raw.githubusercontent.com/shreys7/django-todo/develop/staticfiles/todoApp.png)
### Setup
To get this repository, run the following command inside your git enabled terminal
```bash
$ git clone https://github.com/shreys7/django-todo.git 



It would be best practice always, if we create a new enviornment before running the application. 
Before creating a new enviornment check python3 is installed or not and also pip module need to install.
follow the below steps for installing python3, pip module and creating a new environment.
install python 3.9 as per your linux distribution
install pip module (for python3.9)
install virtual enviornment (venv for RHEL & centos)"# pip3.9 install virtualenv"
create a virtual environment ## python3 -m venv environmentnameasperyourchoice
                             # python3 -m venv appenv (in may case i created a virtual environment as "appenv")
activate your virtual environment : # source appenv/bin/activate   (virtual environment name as "appenv" followed by /bin/activate)
Now go to the directory django-todo where we need to perform all the tasks.
```
You will need django to be installed in you computer to run this app. Head over to https://www.djangoproject.com/download/ for the download guide
# pip install Django  
if any warnings we can upgarde the pip module from lower version to higher version, check warnings.

Once you have downloaded django, go to the cloned repo directory ($ cd django_todo) and run the following command
in my case the cloned repo is django-todo
```bash
$ python manage.py makemigrations
```

This will create all the migrations file (database migrations) required to run this App.

Related issues:
            "SQLite 3.9.0 or later is required (found 3.7.17)."
Solution: 
          sqlite 3.9.0 mobue need to download, install and seup before running database migartion, solution has been found on below link.
          https://programmerah.com/solved-django-core-exceptions-improperlyconfigured-sqlite-3-9-0-or-later-is-required-found-3-7-17-29493/
          
 Afetr all this done make a list requirements, which will help you futufre when it need to recall.
 
 $ pip freeze > requirements.txt  (This is an optional step not mendotary)
                   
Now, to apply this migrations run the following command
```bash
$ python manage.py migrate
```
One last step and then our todo App will be live. We need to create an admin user to run this App. On the terminal, type the following command and provide username, password and email for the admin user
```bash
$ python manage.py createsuperuser
```

That was pretty simple, right? Now let's make the App live. We just need to start the server now and then we can start using our simple todo App. Start the server by following command

```bash
$ python manage.py runserver
```
Once the server is hosted, head over to http://127.0.0.1:8000/todos for the App.

Now the application is running in local host, if you want access from anywhere run as 
$ python manage.py runserver 0.0.0.0:8000
Now the application running in foreground, if you want run this as background run as 
$ python manage.py runserver 0.0.0.0:8000 &       ### (you can use nohup at the begining of the command for an output)
if you want to check the process is running on 8000 port
$ lsof -i:8000
If you want to kill the process 
$ kill -9  4467    (" in my case 4467 is Process ID of the process from above command")
Cheers and Happy Coding :)
TRY WITH DOCKER CONTAINER :
Prerequistes:
  Latest version of docker
$ docker --version
$ systemctl enable docker.service
$ systemctl start docker.service
$ docker ps
$ vi Dockerfile   (recomended to staty in same directory of django-todo)
write inside docker file below scripts
  FROM python:3
  RUN pip install django==3.2
  COPY . .
  RUN python manage.py migrate
  CMD ["python","manage.py","runserver","0.0.0.0:8000"]
  Save and exit (esc :wq)
  Now buitl the docker image form Dockerfile
  
$ docker build . -t todo-app
$ docker ps
$ docker run -p 8000:8000 <container ID>  ## (-p) user for port expose with hots port to container port ##
check application is running with public ip of your machine:8000 (e.g. http://13.127.10*.15*:8000/)
Control + C for stop the running application
if you want to run the application in background 
$ docker run -d -p 8000:8000 <container ID> ## (-d) user for demon run , which allow the application to run in background ##
Now we have successfully ran todo-app in docker container also, Thanks...
