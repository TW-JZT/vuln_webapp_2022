# TrustMave

## TLDR
Docker:  
```
$ docker-compose up --build
```
No Docker:  
```
$ ./setup
$ ./start
```

## Project Info
A social task management platform originally named TaskMaster. 
The code has been modified into TrustMave to add vulnerabilities for study purposes.
 
Credit to the team:
* Jade L
* Solomon C
* Sean C
* Max K
* aaanndd myself ;)

## Vulnerabilities 
| Syntax                                 | Description |
| -------------------------------------- | ----------- |
| XSS                                    | 2           |
| Insufficient session management        | 1           |
| Insufficient authentication management | 1           |
| Sensitive file disclosure              | 1           |
| SSRF                                   | 1           |
| IDOR                                   | 2           |
| Email/Username Enumeration             | 2           |


## Prerequisites
TrustMave requires the following software to be installed on the system.
* Nodejs 10.24.0
* Python 3.7.3 
* Pip 9.0.1
* Sqlite3 3.27.2

Please note that these version are recommended as they are already available on vlab.

## How to run 

You can just run:  
```
$ docker-compose up --build
```

To run the TrustMave for the first time without docker, simply use the following command.
```
# cd to the root directory
$ ./setup
```
This script will:
* Create a python virtual environment (venv)
* Install all required python packages in the venv
* Launch the backend flask server
* Create a logging file for the backend
* Install all npm packages that are required for the frontend
* Launch the frontend
* Create a logging file for the frontend
* Open TrustMave in a web-browser

Once TrustMave is ready and running, users should see a message indicating the url of the website.
<p style="text-align: center;">
<em>Serving frontend at http://localhost:port</em>

An option is also provided to run TrustMave and populate the database.
```
# cd to the root directory
$ ./setup --new
```
Please note that this will overwrite all existing data inside the database. 

When running again, use:  
```
# cd to the root directory  
$ ./start  
```

## Configurations
The flask backend server can be configured using the <em>config.py</em> located in </em>./backend/server/config.py</em>.

It is recommended that user at least configure the following:
* Flask secret keys (for encryption)
* The type of database that’s being used (default to sqlite) 
* The profile picture storage location and allowed extensions
* The email username and password

## Logging
When <em>./start</em> are used to launch TrustMave, backend logs will be recorded in <em>backend/logs.txt</em> and frontend logs will be recorded in <em>frontend/logs.txt</em>.

## Generating Sample Data
A script (<em>sampleData.py</em>) has been provided in the backend directory to populate the database with sample users and tasks. This script will add a few users and tasks. Please however take note that it is recommended that users create their own account to test out the functionalities that require a legitimate email address. 
 
### Credentials
    
Email | Password | Name
--- | --- | ---
test1@gmail.com | 1234 | Monkey Kong
test2@gmail.com | 1234 | Monkey Long
test3@gmail.com | 1234 | Monkey Tong

To run the script:
```
# cd to the backend directory and activate the python venv
$ python3 sampleData.py
```
A flag is also available to populate the database during first start up with /start --new. (For more details please refer to [How to run](#how-to-run))
