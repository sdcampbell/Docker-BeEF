# Docker-BeEF
BeEF customized for your domain name and TLS cert, running in Docker.

## Why?
I like to sandbox pentest tools using Docker to keep my testing environment clean and add aliases to run my Docker images for ease of use. I've tried other BeEF docker images but had issues when I tried to customize them. I wanted to make it easy for others to run BeEF on any system that can run Docker. I configured it to autorun modules that make it useful for capturing admin users when hooked by blind XSS on backend administrative interfaces and getting a screenshot of the page where they were hooked.

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

As configured, your BeEF Docker container will use the autorun.json to take a screenshot of the victim's browser and hook the root of the domain for persistence. Instead of losing the victim when they leave the page, the root of the website is hooked and they stay hooked as long as they're on the site, giving you time to run other modules. (I recommend the 'pretty_theft' Persistence module to prompt the victim to enter creds).

Also see the Notifications extension to receive email, Twitter, or Slack notifications when you hook a new victim: https://github.com/beefproject/beef/wiki/Notifications
