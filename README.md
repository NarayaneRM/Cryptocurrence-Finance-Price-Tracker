# An API Cryptocurrency tracker

Can't be bothered with setting up Docker to test it out? You are in luck. Here you will find an API Cryptocurrency tracker inside the repository infrastrucutre so you can try it out. This will allow you to quickly test the stack to see if it meets your needs. 

[![Try in PWD](https://github.com/play-with-docker/stacks/raw/master/assets/images/button.png)](https://labs.play-with-docker.com/?stack=https://raw.githubusercontent.com/vegasbrianc/crypto-currency-tracker/master/pwd-stack.yml) 

# Pre-requisites

Before we get started installing the Prometheus stack. Ensure you install the latest version of docker and [docker swarm](https://docs.docker.com/engine/swarm/swarm-tutorial/) on your Docker host machine. Docker Swarm is installed automatically when using Docker for Mac or Docker for Windows.

# Installation & Configuration

Clone the project locally to your Docker host. 

Change to the `crypto-currency-tracker` directory and run the following command:

    $ HOSTNAME=$(hostname) docker stack deploy -c docker-compose.yml crypto

That’s it the docker stack deploy command deploys the entire Docker, Prometheus, Grafana and CoinMarketCap stack automagically to the Docker Swarm. 
Wait a minute for everything to download and install


## Check the Status

In order to check the status of the newly created stack:
  
    $ docker stack ps crypto

View running services:
    
    $ docker service ls

View logs for a specific service

    $ docker service logs crypto_<service_name>

## Grafana Configuration

The Grafana Dashboard is now accessible via: `http://<Host IP Address>:3000` for example http://192.168.10.1:3000

    username - admin
    password - foobar (Password is stored in the `config.monitoring` env file)

Now we need to create the Prometheus Datasource in order to connect Grafana to Prometheus 
* Click the `Grafana` Menu at the top left corner (looks like a fireball)
* Click `Data Sources`
* Click the green button `Add Data Source`

# Security Considerations
This project is intended to be a quick-start to get up and running monitoring Crypto Currencies with Docker, Prometheus, and Grafana. Security has not been implemented in this project. It is the users responsibility to implement Firewall/IpTables, SSL, and access control.

Since this is a template to get started Prometheus and Alerting services are exposing their ports to allow for easy troubleshooting and understanding of how the stack works.
