# App that expose API to play with liveness/readiness probes in k8s

The app uses Spring Boot Actuator, these probes are made available under these endpoints:
 - `readiness` probe: `/actuator/health/readiness`
 - `liveness` probe: `/actuator/health/liveness`

## How to use it?

Compile this app using JDK 11+:
```bash
$ ./mvnw clean package
```

Start this app:
```bash
$ java -jar target/spring-k8s-probes-demo.jar
```

Build custom images if needed to test different releases (Use different tags when needed. In this case we used latest):

```bash
$ docker build -t ltozi/k8s-probe-spring:latest .
```

Hint: to make custom images tests locally on minikube you can build images using minikube docker env before making the build

```shell
#first call this line to set the proper local env
eval $(minikube -p minikube docker-env)

#build the image directly into the minikube docker context
docker build -t ghcr.io/ltozi/k8s-probe-spring:latest .

docker push ghcr.io/ltozi/k8s-probe-spring:latest
```