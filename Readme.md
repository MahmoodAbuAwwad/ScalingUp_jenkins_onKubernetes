# ScalingUp_jenkins_onKubernetes

* First, I've build a Docker Image to use within Deployment of Kubernetes
--Steps in DockerFile --> Jenkins Image with some plugins installed 
I use myJenkinsImage from Dockerfile and Jenkins 2.263.2 from JenkinsRepo. 

* jenkins_deployment and jenkins_service yaml files used to deploy and create a jenkis service over kubernetes

* make sure to disable firewall incase you want to install some plugins from Jenkins UI
