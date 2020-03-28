# ServerinteractionDemo

The application exposes a NetworkServer which is able to perform calculations like ADD, DELETE,MULTIPLY & SUBTRACT.

- [Developer Setup](#developer-setup)
- [Running the Application](#running-the-application)
- [Testing](#testing)

## Developer Setup

1. Make sure you have Docker install in your system. Reaf the [guide](https://docs.docker.com/install/) on how to install it.
1. Verify Docker installation
    ```shell script
   $ >  docker --version                                                                              ✔  35s  2.3.7   seo-platform-itier-staging-us-west-2/seo-platform-itier-staging ⎈ 
        Docker version 19.03.8, build afacb8b
    ``` 
1. Update the Submodule dependencies to the latest (If using Git)
    ```shell script
    $ >  git submodule update --recursive --remote
    ```
   
## Running the Application
1. Start the dockerized server using [`Docker Compose`](https://docs.docker.com/compose/).
    ```shell script
    $ >  docker-compose up --build -d                                                                    INT ↵  2.3.7   seo-platform-itier-staging-us-west-2/seo-platform-itier-staging ⎈
    ```
1. This will build both the NetworkServer & DataServer
    ```shell script
    Building network
         Step 1/7 : FROM openjdk:8u121-jre-alpine
          ---> 319698b3b71a
         Step 2/7 : MAINTAINER Vedang Sharma
          ---> Using cache
          ---> 901785773932
         Step 3/7 : WORKDIR /var/network-api
          ---> Using cache
          ---> c8de086a1b45
         Step 4/7 : ADD target/NetworkServer-1.0-SNAPSHOT.jar /var/network-api/NetworkServer-1.0-SNAPSHOT.jar
          ---> Using cache
          ---> f4338f0612f4
         Step 5/7 : ADD config-docker.yml /var/network-api/config.yml
          ---> Using cache
          ---> 821e608e81f8
         Step 6/7 : EXPOSE 9090 9091
          ---> Using cache
          ---> 39ff5ea1b87f
         Step 7/7 : ENTRYPOINT ["java", "-jar", "NetworkServer-1.0-SNAPSHOT.jar", "server", "config.yml"]
          ---> Using cache
          ---> 8ca9611803d9
         Successfully built 8ca9611803d9
         Successfully tagged serverinteractiondemo_network:latest
         Building data
         Step 1/7 : FROM openjdk:8u121-jre-alpine
          ---> 319698b3b71a
         Step 2/7 : MAINTAINER Vedang Sharma
          ---> Using cache
          ---> 901785773932
         Step 3/7 : WORKDIR /var/network-api
          ---> Using cache
          ---> c8de086a1b45
         Step 4/7 : ADD target/DataServer-1.0-SNAPSHOT.jar /var/network-api/DataServer-1.0-SNAPSHOT.jar
          ---> Using cache
          ---> 516dc2f536db
         Step 5/7 : ADD config.yml /var/network-api/config.yml
          ---> Using cache
          ---> 9e601db3058f
         Step 6/7 : EXPOSE 9000 9001
          ---> Using cache
          ---> dbcd9135065a
         Step 7/7 : ENTRYPOINT ["java", "-jar", "DataServer-1.0-SNAPSHOT.jar", "server", "config.yml"]
          ---> Using cache
          ---> de472099942a
         Successfully built de472099942a
         Successfully tagged serverinteractiondemo_data:latest
         Starting serverinteractiondemo_network_1 ... done
         Starting serverinteractiondemo_data_1    ... done
    ```

## Testing 

The app offers the [Swagger](https://swagger.io/) implementation of the available endpoint. You can access it by navigating to
[`http://localhost:9090/swagger`](http://localhost:9090/swagger).
