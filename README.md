# kubernetes-Helm-charts

# Helm chart is the package manager for kubernetes. Its like 'chocolatey' for windows.'apt','yum' for linux.

# For example if you want a mysql service needs to be run in your kubernetes cluster, we have done is we created YAML file we created persistent volumes, persistent
# volume claims, CPU memory requests, configmaps, secrets, replication strategies etc... and all those things. 
# The same task will be done in HELM CHART with simple command. helm will take care of everything for you staring from creating more professional YAML files,
# strategies and everything.


![image](https://user-images.githubusercontent.com/80065996/150290239-8d8e810f-9188-46fa-ae2d-d63bb7b0f08e.png)


# version of Helm package manager we are using, we can check using below command


![image](https://user-images.githubusercontent.com/80065996/150292690-58d82564-6310-4983-bcc4-dc00c50d64cc.png)


# Important sites:

https://artifacthub.io/      --> We can get different package implementations like images for docker in dockerhub

https://github.com/helm/helm/releases     ---> download site for helm. we can download file extract it set the path and thats all

# Active version of helm now

# Helm version 2 is now not in use. it works by installing pod as daemon sets called 'Triller'. now 'Triller' is deprecated.


# How to find Kubernetes helm charts.? 


![image](https://user-images.githubusercontent.com/80065996/150294737-a5532060-6602-46d4-a05e-1ef933965287.png)


for example, if you need mysql Cluster,


![image](https://user-images.githubusercontent.com/80065996/150294836-4e31777d-1bfd-4244-bffa-ebe2496b4465.png)


Just follow the steps in the site,


![image](https://user-images.githubusercontent.com/80065996/150294936-09d14338-b3e2-491e-85b3-b4f21188cce2.png)


# Step1 : Adding a repositories,


![image](https://user-images.githubusercontent.com/80065996/150295442-f48f317a-f0b6-40b0-8174-eb9140eaac55.png)


# step2 : Install the mysql helm chart


![image](https://user-images.githubusercontent.com/80065996/150305007-b232810f-0e93-4180-86d0-6f5112797534.png)


this will give a pageful of info on how to use this helm chart in our application.


# step 3 : 'Kubectl get all' command to check helm chart is installed successfully


![image](https://user-images.githubusercontent.com/80065996/150305787-cb909f43-f9ee-4c63-a245-b83fc05cd71b.png)


all the components (pods,services, stateful sets) are created successfully as shown above


# step 4 : Command to check what are all the helm charts we have deployed and used till now


![image](https://user-images.githubusercontent.com/80065996/150306359-2955a9d9-ef7a-490e-bc6f-da648fba80ac.png)


# how to uninstall helm chars currently we deployed and used
# command: "helm uninstall name of the chart"


![image](https://user-images.githubusercontent.com/80065996/150306730-151983d6-86f4-4b6d-a6f2-cee55fbb9db7.png)


![image](https://user-images.githubusercontent.com/80065996/150306990-a5069332-3599-440b-9fd3-1d8520a305e0.png)


Checking everything is uninstalled and cleaned,


![image](https://user-images.githubusercontent.com/80065996/150307151-8b38c8b3-fe4f-4c30-bf0d-8556cff113a4.png)


# Notice : What is Artifact hub and what are the politics behind it

before seeing that just see the below result on helm repo list. below command shows what are the repos we installed while installing various hel charts


![image](https://user-images.githubusercontent.com/80065996/150309999-a8621d4c-6934-428b-b68f-b161f9465e13.png)


for the same command in the previous helm version, we will get extra one line with stable version like below,


![image](https://user-images.githubusercontent.com/80065996/150310200-1b410fd5-56de-4b8d-9dc5-78af80a4a276.png)


copy paste the URL of stable version, 

https://charts.helm.sh/stable/

this is the website where we have all stable installation of whatever we needed in kubernetes. these are developed by experts. They dont have any malware or anything
but due to huge maintanence cost, they cannot maintain this and left. then this artifcat hub came into picture. artificat hub is like docker hub, since its 
public hub, everyone can create their own charts and publish it. But as a user while we use this for any of the chart we are planning to use (for example 'MY SQL') we
need to first check the company who created the chart and investigate on our own before using the chart.



