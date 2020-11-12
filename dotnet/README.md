#How to use SingleSimpleServiceDockerfile

1) Copy SingleSimpleServiceDockerfile into your root folder and rename it to Dockerfile
2) Change ENTRYPOINT to the your one
3) Build an image with the next command: docker build -t ${serviceName}:${version} (If you use container registry ${dockerRegistry}/${serviceName}:${version} will be better, 
   e.g. devcompanynamedockerregistry.azurecr.io/testservice:1.1.0)
4) To run container with the previously built image use the next command: docker run -p ${externalport}:${internalport} ${imagename}:${version} (e.g. docker run -p 3333:80 demoService:1.1.0)
5) To do it in an interactive manner use -it parameter (e.g. docker run -p 3333:80 -it demoService:1.1.0)
6) Check all containers use the next command: docker ps -a
7) To build an image with the test runner use the next command: docker build --target testrunner -t ${serviceName}:${version} (If you use container registry ${dockerRegistry}/${serviceName}:${version} will be better, 
   e.g. devcompanynamedockerregistry.azurecr.io/testservice:1.1.0)
8) To run tests from the built test container use the next command: docker run ${imagename}:${version} (e.g. docker run demoService:1.1.0) #you can use -it for interactive run
9) To copy test results use the next command: docker cp ${containerName}:/project/test-results ${destinationFolder} (e.g. docker cp test-container:/project/test-results test-results)
10) To prune unused docker images and containers use the next commands: docker image prune, docker container prune 
