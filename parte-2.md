# Admin Khipu web

This is a web used for user and projects management of Khipu HPC cluster. It was develop using Django and PostreSQL as a database.

## How to setup locally?

We have two options to setup. The first one is to setup directly using a virtual environment and the other is using docker.

**Setup using virtualenv:**

- Download the repo, locate to the project root and create a virtual environment using Python 3.

```bash
# Setup the virtualenv
python -m venv venv
source venv/bin/activate

# Install reqs
pip install -r requirements.txt
```
- Setup the enviroment variables in a `.env` file using the following format:

```bash
SECRET_KEY=<a new secret>
DEBUG=True
EMAIL_USE_TLS=True
EMAIL_HOST=smtp.googlemail.com
EMAIL_PORT=587
EMAIL_HOST_USER=khipu@utec.edu.pe
EMAIL_HOST_PASSWORD=<khipu email password>
DB_NAME=<khipu db name>
DB_USER=<khipu db user>
DB_PASSWORD=<khipu db password>
DB_HOST=<khipu db host>
DB_PORT=<khipu db port>
DOCS_URL=https://docs.khipu.utec.edu.pe
LDAP_URI=<ldap URI>
LDAP_USER=<ldap user>
LDAP_PASSWORD=<ldap password>
LDAP_DC=<ldap dc>
LDAP_USER_GID_NUMBER=<ldap GID Number>
ALLOWED_HOSTS=localhost,127.0.0.1
CSRF_TRUSTED_ORIGINS=http://localhost,http://127.0.0.1
```

- Create a superuser (only the first time)

```bash
python manage.py createsuperuser
```

- Apply migrations 

```bash
python manage.py migrate
```

- Run the server

```bash
python manage.py runserver
```

**Setup using docker**

- Create the `.env` file with the same format as aforementioned.
- Build the docker image

```bash
docker-compose build
```

- Execute the image

```bash
docker-compose up -d
```

- Create the superuser (only the first time)

```
docker exec -it <docker container id> bash
python manage.py createsuperuser
```