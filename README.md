# Linux Server Configuration

This project takes a baseline installation of a Linux distribution on a virtual machine and prepares it to host an existing [RESTful web application](https://github.com/seon-/catalog), secures it from a number of attack vectors, and configures it with a database server.

## Project Details

1. IP Address: 34.222.11.27
2. SSH Port: 2200
3. URL: http://34.222.11.27.xip.io/

### Summary

Below is a summary of steps taken to successfully deploy the web app, including software installed and configuration changes made.

#### Procured Server
- Started a new Ubuntu Linux server instance on Amazon Lightsail.

#### Secured Server
- Updated all currently installed packages.
- Changed the SSH port from 22 to 2200 and configured the Lightsail firewall to allow it in the Networking dashboard.
- Configured the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).
- Secured public keys.
- Disabled `root` remote login and enforced key-based SSH authentication.

#### Gave `grader` Access
- Created a new user account named `grader` with permission to sudo.
- Created an SSH key pair for grader using the ssh-keygen tool.

#### Prepared to Deploy Project
- Configured the local timezone to UTC.
- Installed and configured Apache to serve a Python mod_wsgi application.

#### Installed and Configured PostgreSQL Database Server
- Configured database server to serve data.
- Ensured no remote connections allowed.
- Created a new database user named `catalog` with limited permissions to the `api` application database.

#### Deployed Project
- Installed git and ensured `.git` directory not publicly accessible via a browser.
- Cloned the web app and created a virtual environment to install app requirements.
- Configured web server to serve the web application as a WSGI app.
- Updated OAuth credentials on Google with new host name and integrated new JSON.


## Third-Party Resources
- Digital Ocean, [How To Deploy a Flask Application on an Ubuntu VPS](https://www.digitalocean.com/community/tutorials/how-to-deploy-a-flask-application-on-an-ubuntu-vps)
- Digital Ocean, [How To Secure PostgreSQL on an Ubuntu VPS](https://www.digitalocean.com/community/tutorials/how-to-secure-postgresql-on-an-ubuntu-vps)
- Official PostgreSQL Documentation, [postgresql.org](https://www.postgresql.org/)
- Stack Overflow, [Google: Permission denied to generate login hint for target domain NOT on localhost](https://stackoverflow.com/questions/36020374/google-permission-denied-to-generate-login-hint-for-target-domain-not-on-localh)
- Udacity Knowledge Platform:
  - ImportError: cannot import name 'app': https://knowledge.udacity.com/questions/20361
    - Referenced in answer: https://github.com/jaysimonkay/Linux-Configuration
  - How to setup database, https://knowledge.udacity.com/questions/21727
  - Internal server error, https://knowledge.udacity.com/questions/10996


## Contributing

Pull requests will not be accepted, as this project was created for the FSND Udacity program.

For details, check out [CONTRIBUTING.md](CONTRIBUTING.md).