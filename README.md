# CybersecurityStarterKit

New implementation with many more features and simplified questions compared to
the Startup security kit.



## Deploy with a Dockerized environment (for development purposes)

### Install Docker

- [Get started](https://docs.docker.com/get-started/);
- [Manage Docker as a non-root user](https://docs.docker.com/install/linux/linux-postinstall/)


### Start the containers


```bash
$ docker-compose build
$ docker-compose up -d
```

The server will be listening at http://127.0.0.1:8000.


## Deploy manually

### Requirements

```bash
$ sudo apt install npm gettext # later: postgresql
```


### Set up your Python environment

Before to begin you will need to install
[pipenv](https://github.com/pypa/pipenv).  
A convenient way to do so is to first install
[pyenv](https://github.com/pyenv/pyenv). With pyenv you will be able
to easily manage Python versions on your system and to install the latest
version of Python:

```bash
$ pyenv install 3.7.4 # install Python
$ pyenv global 3.7.4 # make this version default for the whole system
$ pyenv versions # check
```

Then install
[pipx](https://github.com/pipxproject/pipx).  
And finally install pipenv with pipx.

Later on, this Python environment can be used on production with for
example WSGI.


### Install the application


```bash
$ git clone https://github.com/CASES-LU/CybersecurityStarterKit.git
$ cd CybersecurityStarterKit/csskp
$ npm --prefix ./static install ./static
$ pipenv install
```


### Configure and run the application

Still in the folder `csskp`:

```bash
$ pipenv shell
$ python manage.py compilemessages # compile the translations
$ # I suppose we need to initialize the DB with manager.py...
$ python manager.py createsuperuser --username <username>
$ python manager.py runserver # not for production
```



## Upgrading the application

### Updating the models

```bash
$ cd CybersecurityStarterKit/
$ git pull origin master
$ cd csskp/
$ pipenv shell
$ python manage.py makemigrations
$ python manage.py migrate
```


### Internationalization

Simply compile the new translations:

```bash
$ python manage.py compilemessages
```

If you want to update the translations, you must first run:

```bash
$ python manage.py makemessages # extract the translations
```

Then you can use a tool like
[poedit](https://poedit.net) to translate the strings and you can compile with
the previously mentioned command.



## License

This software is licensed under
[GNU Affero General Public License version 3](https://www.gnu.org/licenses/agpl-3.0.html)

* Copyright (C) 2019 SMILE gie securitymadein.lu
