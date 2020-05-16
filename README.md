# docker-elkstack
ELK stack deployment through docker-compose.

**Prerequisites:**

1. docker (docker for windows)
2. docker-compose

## How to deploy ELK stack

First off all! as this example is based on Docker for Windows (Linux Mode), you have to swicth your deamon to linux container mode

Then open command line in the directory where you clonned this repository and just execute following command and it will up your elk stack and you can browse your kibana dashboard at [http://localhost:5601](http://localhost:5601)

```
docker-compose up -d
```

Once ELK stack is up then you can deploy your app which logs you want to monitor through elk stack/kibana.
For that puporse you have to route your container logs to tcp://localhost:8089 and logstash will capture those logs and then send to elasticsearch which will finally shows the logs in a pretty format on kibana.

> I have used the voting app which is a multi-tier application and its complete code can be found at [github.com/dockersamples/example-voting-app](https://github.com/dockersamples/example-voting-app)

## Deploying voting app through docker
Once you have cloned the voting app repository on you system then you have to place docker-compose-voting-app.yml into that repository and just run the following command and it will live your application at [](http://localhost:5000)
Once you have cloned the voting app repository on you system then you have to place docker-compose-voting-app.yml into that repository and just run the following command and it will live your application at [http://localhost:5000](http://localhost:5000)

```
docker-compose -f docker-compose-voting-app.yml up -d
```

In the `docker-compose-voting-app.yml`, i have made some changes to route/export logs to the logstash server and made this stack part of already existing elk stack so that all the services can communicate easily.