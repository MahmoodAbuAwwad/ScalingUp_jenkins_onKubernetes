# ScalingUp_jenkins_onKubernetes

* First, I've build a Docker Image to use within Deployment of Kubernetes
--Steps in DockerFile --> Jenkins Image with some plugins installed 

I use myJenkinsImage from Dockerfile and Jenkins 2.263.2 from JenkinsRepo. 

* jenkins_deployment and jenkins_service yaml files used to deploy and create a jenkis service over kubernetes

* jenkins ClusterRoleBinding and Jenkins ServiceAccount to give authorize jenkins master inside the cluster

* make sure to disable firewall incase you want to install some plugins from Jenkins UI

* Manage Nodes - Cloud Config. 
  Add Kubernetes Cluster and Jenkins server and Tunnel


* Set Master Exexcutor to Zero

* JenkinsUI -> Manage Jenkins -> Nodes -> Clouds 

setup kubernetes as cloud - where
 * Kubernetes URL---> kubectl cluster-info 
 * Jenkins URL --> kubectl describe <JenkinsPod> | grep IP

