# Docker-BeEF
BeEF customized for your domain name and TLS cert, running in Docker.

## Installation:

`git clone https://github.com/MooseDojo/Docker-BeEF.git`

Copy your LetsEncrypt certs to the directory as fullchain.pem and privkey.pem.

Edit config.yaml, replace three instances of 'changeme' with your desired password, public hostname, and CORS allowed domains.

Note: If you plan to expose this to the Internet, edit config.yaml and replace permitted_ui_subnet 0.0.0.0/0 with your IP address /32.

## Build:

`docker build -t [name]/beef .`

Example `docker build -t scampbell/beef .`

## Run:

`docker run --rm -it -p 3000:3000 -p 6789:6789 -p 61985:61985 -p 61986:61986 scampbell/beef`

To make future use easier, alias the command in your .bashrc file.
