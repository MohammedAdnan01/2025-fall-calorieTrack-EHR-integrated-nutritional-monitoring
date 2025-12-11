## ⚙️ Installation

Two step setup, first install the **prerequisites** then setup the **project**.

### Prerequisites

#### Install Docker

Install docker for you operating system, follow: [Install | Docker Docs](https://docs.docker.com/get-started/get-docker/).
Additionally, install Docker Desktop [Install | Docker Desktop](https://docs.docker.com/desktop/).

Test if docker engine is running and accessibe from terminal

```bash
  docker ps
```

#### Install Python

Install python (Recommended v3.10.12) in your system [Install | Python](https://www.python.org/downloads/release/python-31012). For windows users, if required add python to path [stack-overflow](https://stackoverflow.com/questions/3701646/how-to-add-to-the-pythonpath-in-windows-so-it-finds-my-modules-packages). Check installation using:

```bash
  python --version
```

#### Install Git and Git Bash

Install git and git bash. [Install | Git](https://git-scm.com/downloads)

### GCP Access

Request and get access to GCP from VosynVerse TL/DTL or your pod captain.

Once you have GCP access install GCP CLI by following [GCP CLI](https://cloud.google.com/sdk/docs/install). Login to GCP using the commands below.

⚠️ **Important:** Windows users must run this using **Powershell**.

```bash
  gcloud auth application-default login
```

### Setup

⚠️ **Important:** Windows users must run this in **Git Bash**. If u run this in powershell, the script will not work.

Run the setup script:

```bash
  ./setup.sh
```

If you receive an error about permissions, enable execute permission on the file:

```bash
  sudo chmod +x setup.sh
```

All the setup scripts must be run from project root directory unless otherwise specified.

Expected files and directories:

```bash
config
├── config.ini.example
├── env
│  ├── app.env
│  ├── db.env
│  └── ts.env
compose.yaml
compose.gcp.yaml


vv_backend
└── vosyn_assist
│   └── AI_assisted_chat_search
│       └── .env
```

If you dont have GCP access, open `compose.gcp.yaml` and comment out the `volumes` and `environment` sections.

#### 🚀 Run project

Build images:

```bash
  docker compose build
```

Run the project:

```bash
  docker compose up
```

You should see three services running: `app-1`, `db-1`, `redis-1`, `pga-1` and `ts-1`.

Server runs on http://localhost:8000/. This is the `api-base-url`.

## 📖 API Documentation

API Documentation can be accessed by visiting:
http://localhost:8000/swagger/
or http://api.vosynverse.com/swagger/

## Extensions

Install the extension 'ruff' on VSCode. If you are using a different IDE like pycharm or zed, install ruff extension there.

> Install 'ruff' extension for VSCode

## Setup PgAdmin (Dockerized)

You don't need to install pgadmin locally, it runs automatically when you run the services.

To access pgadmin, in your browser visit: http://localhost:5050/

Login to pgadmin using the following credentials:

```
Username: admin@example.com
Password: admin123
```

Click 'Add New Server' and enter the following credentials in the general and connections tab:

```
Name: vosynverse_db
Host name/address: db
Username: vvuser
Password: vvpassword # remember to tick the 'save password option'
Post: 5432
```

You are all done, vosynverse_db should appear as a database under 'servers'. You won't have to setup or login the next time you run the services.

## Managing Database Migrations

Documentation to be written...

## Known Issues

> _"app-1 | UserWarning: Your application has authenticated using end user credentials from Google Cloud SDK without a quota project. You might receive a "quota exceeded" or "API not enabled" error._"

Can be ignored for now. If required to solve this, you will need to set quota-project in your gcp credentials.
