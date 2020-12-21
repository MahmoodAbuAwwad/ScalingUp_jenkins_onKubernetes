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
 * Jenkins URL --> kubectl describe <JenkinsPod> | grep IP  --> IP of jenkins Pod





-------------------------------------
-----------------------------------



In case the Jenkins master is outside the cluster (not a pod inside Cluster)



U need to use certificates as Credentials to your jenkikns configrations in UI
Please see https://paranoiaque.fr/en/2019/07/14/run-jenkins-jobs-on-kubernetes/




CONFIG=".kube/config"

echo -n $(cat $CONFIG | grep certificate-authority-data | cut -d: -f2) | base64 -d > ca.crt

echo -n $(cat $CONFIG | grep client-certificate-data | cut -d: -f2) | base64 -d > client.crt

echo -n $(cat $CONFIG | grep client-key-data | cut -d: -f2) | base64 -d > client.key

openssl pkcs12 -export -out cert.pfx -inkey client.key -in client.crt -certfile ca.crt


rm client.crt client.key

-----------------
* Enter the following parameters:

Kubernetes URL: your Kubernetes server API url, you can find it in .kube/config, line server

Kubernetes server certificate key: the content of the previously generated file ca.crt

Credentials: select your Kubernetes certificate, the one we have added previously

Jenkins URL: the URL to access to your Jenkins server


use jenkinsci/jnlp-slave as pod template's Image
open port 40241 on master jenkins
