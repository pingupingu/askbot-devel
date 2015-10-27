
Askbot Installation:
--------------------

Install and run the askBot project

Setup server environment:
-------------------------

Tested installation on ubuntu 15.10

Install linux packages:
-----------------------
~ $ sudo apt-get install libjpeg62 libjpeg-dev

Install pip
-----------

NOTE: if ‘which pip’ returns a path to pip, it is already installed. If it is not installed, follow these instructions:

get ‘ez_setup.py’:

~ $ wget https://bootstrap.pypa.io/ez_setup.py -O - | sudo python

verify easy install:

~ $ which easy_install
/usr/local/bin/easy_install

install pip:

~ $ sudo easy_install pip

Install virtualenwrapper:
-------------------------
~ $ sudo apt-get install virtualenvwrapper

Create a new Environment:
-------------------------
~ $ mkvirtualenv askbotEnv

Switch to the new Environment:
------------------------------
~ $ workon askbotEnv

Git setup:
----------
~ $ git clone https://github.com/pingupingu/askbot-devel.git

Working on askbot:
------------------
~ $ cd askbot-devel
~ $ pip install -r askbot_requirements
~ $ python setup.py develop
~ $ askbot-setup ## and follow the prompts with an <install directory> and postgresql database as setup below

Setup postgresql with user: askbotuser and password: askbotpassword on database: askbotd
----------------------------------------------------------------------------------------
~ $ sudo -iu postgres
~ $ psql -c 'CREATE USER askbotuser WITH PASSWORD 'askbotpassword';
~ $ psql -c "CREATE DATABASE askbotdb WITH OWNER askbotuser;"

Running askbot on port 10000:
-----------------------------
~ $ cd <install directory>
~ $ python manage.py collectstatic ## test to make sure everything is OK

~ $ python manage.py runserver 127.0.0.1:10000 ## run on port 10000

Then open the http://127.0.0.1:10000 on the browser and create/signup as a new user

