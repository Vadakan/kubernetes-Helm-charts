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


# creating monitoring stack using helm chart (promotheus to minotor the nodes of cluster and grafana-UI for promotheus)

# Our needs to set up Monitoring system :

1) Prometheus - to monitor the nodes
2) Grafana  - UI to see what is happening in Pomotheus
3) Alert manager - alert manager system for cluster monitoring system


**Step 1: # search for the word Monitoring to see what are results its showing. There are no monitoring stack with promotheus so we will skip to step 2**


![image](https://user-images.githubusercontent.com/80065996/150628390-ceb674cc-bff2-420b-9d41-8c2fd2bc4e33.png)


**step 2: # search for the word Prometheus to see result list. We need not only need prometheus. We need grafana as well. so we are not planning to install
promotheus alone separately. We need to install in combination**

# We selected Kube-Promotheus-stack for the purpose.


![image](https://user-images.githubusercontent.com/80065996/150628742-97ad6dc4-9858-4b3f-8b45-26994187149c.png)


# step 3 :In the website, first thing we need to add the repo.


![image](https://user-images.githubusercontent.com/80065996/150629297-e0e88c56-65e0-4476-86a7-0b28d4f987d7.png)


Slight change in the command for creating the repo. Repo name we can give anything we want,


![image](https://user-images.githubusercontent.com/80065996/150629315-58c233d9-d89c-41f8-a21c-828bbc23b7a6.png)


**We can check the repos created by using below command**


![image](https://user-images.githubusercontent.com/80065996/150629365-a3e00205-64d5-4240-886b-8ecba325b48e.png)


**note : **
**1) "Helm repo list" -- to see the repos used to create the helm charts**
**2) "Helm list" -- to see the list of helm charts installed in the cluster**

If we take the link of repo and put it in browser, you can see the details about that helm chart


![image](https://user-images.githubusercontent.com/80065996/150630132-e79a949b-c346-4154-9350-e27a5da910cd.png)


**Step 4: Do the repo update. It is good practise the update the repo before installing helm chart**


![image](https://user-images.githubusercontent.com/80065996/150630175-eb23acee-f130-4881-bdd2-39ca40610401.png)


![image](https://user-images.githubusercontent.com/80065996/150630162-da5af50d-3cff-44c9-b0f8-8fdce129201f.png)


# This command updated all the repos available in the kubernetes cluster


![image](https://user-images.githubusercontent.com/80065996/150630202-d288594c-ff55-4a9f-a978-1e4feb613c14.png)


# step 5 : Repo is set up successfully. Now we have to install helm chart


![image](https://user-images.githubusercontent.com/80065996/150630350-9dfd947b-1453-4ecb-a2a3-d83c892e5609.png)


# We need 3 parameters.
# Release_name => what do we need to call this release.
# Repo-name := repo we used for this stack.
# Stackname := stack name from artifcat hub

for us :=
**helm install monitoring prom-repo/kube-prometheus-stack**

# Monitoring - we ca give any name we want.name of the release we are going to perform. We are going to create a monitoring system. so it is called as 'Monitoring'. 
# prom-repo - name of the repo
# kube-promotheus-stack - name of the helm chart from artifcat hub


![image](https://user-images.githubusercontent.com/80065996/150630504-171589e5-b693-4f1b-b262-ba8260f384b5.png)


# you can see now promotheus stack is installed sucessfully, 


![image](https://user-images.githubusercontent.com/80065996/150631020-76fea47f-2222-4bab-8d28-bc0727a7545f.png)


# you can notice now promotheus is installed in 'default' namespace as shown below,


![image](https://user-images.githubusercontent.com/80065996/150631119-961e82b2-e328-4bd7-99ec-1156f0dbf892.png)


![image](https://user-images.githubusercontent.com/80065996/150631171-1e26f4a7-fdbe-4d2c-baec-5a5b39edad8d.png)


# the release name 'monitoring' used while installing the helm chart will be created as labels in the pod created for the helm chart
# below command uses label "release=monitoring" to get the pods assciated with it


![image](https://user-images.githubusercontent.com/80065996/150631189-87f469cf-aa1d-4ec6-8424-0340271af335.png)


# Now we installed monitoring system with alert manager using prometheus and grafana. Services created for the same seen below,


![image](https://user-images.githubusercontent.com/80065996/150631340-68430cf7-ea30-46fc-9b9f-4bfc13f0951e.png)


As we know, the service 'monitoring grafana' as shown above is the frontend. This is created as 'clusterIP' so we cannot access from browser outside.


# so we are planning to edit that service in a dirty way. Please dont ever use 'kubectl edit' in your project. just for practising we are using this command
# it will pop the YAML file for the service. we can edit it now


![image](https://user-images.githubusercontent.com/80065996/150631676-387a0c63-7841-4168-b96d-01c35ad382f5.png)


![image](https://user-images.githubusercontent.com/80065996/150631711-0d97ebb4-c7a3-475b-810c-429c50d76e4b.png)


# we can change the 'ClusterIP' to 'NodePort' now and also port number as '300020'


![image](https://user-images.githubusercontent.com/80065996/150631977-ba0d7e7a-cacd-4ccc-be40-2a2158be5221.png)


![image](https://user-images.githubusercontent.com/80065996/150631989-38dd3c21-71c9-4879-b059-ed0991bcfebb.png)


# note: if you do any mistake, the file will not get saved and it will throw error. the file open again automatically for edit. you can check the error
# top of the file, correct the errors and save it
# Now you can see YAML changed we have done applied automatically and 'ClusterIP' changed to 'NodePort'.


![image](https://user-images.githubusercontent.com/80065996/150632196-c106c758-75ef-404e-9ca3-fe7978891949.png)


# take minikube up and type it in browser, you can see grafana frontend


![image](https://user-images.githubusercontent.com/80065996/150632258-3739b6e6-548b-4873-b325-67043d0b5f97.png)


# Note: you cannot use username and password to login into grafana. Because we are not yet configured on this part. its just a skeleton we installed.


![image](https://user-images.githubusercontent.com/80065996/150633023-110afe1f-e655-406b-8606-06564be15c88.png)



# WORKING WITH HELM CHART VALUES. TILL NOW WE KNOW HOW TO CONFIGURE GRAFANA. WE SAW THE FRONTEND. IF YOU GIVE USERNAME AND PASSWORD IT WILL NOT WORK
# BECAUSE WE DIDNT CONFIGURE IT NOW. FOR THAT WE HAVE TO WORK WITH CHART VALUES. 

# helm show values repo-name/stackname - helm show values prom-repo/kube-prometheus-stack
# it will show big list of displays as shown below in the screenshot. 
# These displays are the properties of the chart we are installing. (we can even use the property name while using install command to set the value for property)


![image](https://user-images.githubusercontent.com/80065996/150632729-f54cb28c-fb9e-440f-a61e-476720f9bb95.png)


# due to massive amount of displays for this command, we can really read thru all the comments. so redirect the result commands into the file using command


![image](https://user-images.githubusercontent.com/80065996/150633108-aa8dce7b-9706-4d32-a51f-0b006bf287da.png)


# open the 'values.yaml' in any text editor.
# search for the keyword 'password'. found password related details in 651 lines of the YAML file. Now we identify the propertyname. we can either 
# alter the value of the property in the file itself or get the property name and use the command to alter it


![image](https://user-images.githubusercontent.com/80065996/150633261-c91a51d0-c593-48bb-ab45-5cbf058b9859.png)


![image](https://user-images.githubusercontent.com/80065996/150633436-88dcb284-8f08-4d81-89a5-77113faf5104.png)


# Change the password (we got property name in previous step), so with that we are going to set password for grafana using below command


![image](https://user-images.githubusercontent.com/80065996/150633561-be60cb5a-e886-4897-9eb1-1690eeb9e748.png)


![image](https://user-images.githubusercontent.com/80065996/150633640-6acf33b0-2e96-4d1e-868e-dff9833726ba.png)


# we could see we upgraded the helm chart now. (we changed the propery - updated the password). so it is showing 'revision-2' and status 'deployed' in the result
# comments


# Note: Once we upgraded, you can see by design 'grafana frontend' service is changed from nodePort to ClusterIP again(re-applied). we changed that
# in previous step from ClusterIP to nodePort to test the grafana frontend service.


![image](https://user-images.githubusercontent.com/80065996/150633831-561f3da0-1b2f-42cd-8c25-26dc983281c4.png)


# again i followed the step of kube-edit command to chaned the nodeport and set the port as shown below:


![image](https://user-images.githubusercontent.com/80065996/150633925-c73cfd72-153e-46ba-a67f-4b678773a975.png)


![image](https://user-images.githubusercontent.com/80065996/150634004-3e5ca8b1-bdcf-4e3b-a1f1-06c4af0dd0b0.png)


# now check the username and password in grafana


![image](https://user-images.githubusercontent.com/80065996/150634029-9ba74fc7-b76f-4704-a49d-2d18d9aa5abc.png)


# Note: the Big mistake while updating the properties of YAML file (admin password)
# we should notice in YAML we can create parent and child fields. and if you want to alter the child value we have to refer the parent with dot operator(.) with\
# child to change it. Here the exact problem happened. we altered the password parameter of the child but we didnt refer the parent under which child is present


Parent name is 'grafana', child 'adminPassword' is present under the Parent 'grafana'.


![image](https://user-images.githubusercontent.com/80065996/150634329-aaba5333-c087-4391-ab79-b123b64461d0.png)


# this time using parent child replationship:


![image](https://user-images.githubusercontent.com/80065996/150634411-7c674e75-105f-4ad2-8a44-2d3632e99384.png)


# upgraded,


![image](https://user-images.githubusercontent.com/80065996/150634500-6f6e0693-c10b-4b93-8141-c05b294a42b0.png)


# modify ClusterIP of grafana to nodeport 


![image](https://user-images.githubusercontent.com/80065996/150634567-0a325a0b-e97d-452b-b4e4-8086dce30f5c.png)


![image](https://user-images.githubusercontent.com/80065996/150634602-f373b5f8-7672-4042-b067-295d6f60bb41.png)


# now logged in successfully and it is asking us to set new password


![image](https://user-images.githubusercontent.com/80065996/150634649-07b32d51-d194-4b62-b34f-a74ad5b3af66.png)


# pod is getting terminated and restarted again for new changes. so it is clear that our changes are picked up. Last time pods were not getting restarted.
(all will happen on a flash)


![image](https://user-images.githubusercontent.com/80065996/150634747-296d9f04-206a-4170-93ba-454a4e884e04.png)


# How to change Nodeport in our kube-prometheus helm chart without using 'kubectl edit' command ?
# We used a command 'helm show values' which gave very big YAML file of the helm chart we installed in 'values1.yaml' file. in that file we have to 
# go thorugh and identify parent field and corresponding field for setting NodePort. it is very hard to go through all the lines in the file.
# use ctlf+F (search) option. if still no luck , check for github documentation created for the particualr chart which provided configuration details


luckily for us grafana developer of the chart provided github documentation page: https://github.com/grafana/helm-charts/tree/main/charts/grafana


below details provided in github page,


![image](https://user-images.githubusercontent.com/80065996/150670521-f9d37109-5262-4eaf-b2c6-82e2a790b7c2.png)


# since we identified the field for nodeport, we can pass via command shown in below image and do that. But the problem is command will become big if we want to 
# change the configuration for many values.


![image](https://user-images.githubusercontent.com/80065996/150670724-ee4b3ffa-50e2-43e0-83fa-8d4ef6de02ee.png)



# so we can use Values1.Yaml file we have created and made the edit of configuration we want and there is an option to pass the 'values1.yaml' as an argument to 
# 'helm upgrade' command to make the change


# Changed the 'service' details like below under 'service' section:


![image](https://user-images.githubusercontent.com/80065996/150670874-4ae6c8cd-edcb-4f7a-9e3a-fe6f76f3f441.png)


# also change the admin password field,


![image](https://user-images.githubusercontent.com/80065996/150670945-7df5a1c9-d5aa-4e3a-8ffd-8204a68bb897.png)


# Save the file ,

# now change the 'helm upgrade' command like shown in below image,


![image](https://user-images.githubusercontent.com/80065996/150671016-ae292c49-7f41-4b4a-a1aa-88d1cffbaa6d.png)


# Result: Grafana frontend will be changed from 'ClusterIP' to 'NodePort'.(having some space issue with minikube but in realtime it will change)


![image](https://user-images.githubusercontent.com/80065996/150671787-63a3160a-3946-40bf-9687-d0541119bd93.png)



# Remove all the contents from 'values1.yaml' and keep only 'service' part of 'grafana' and perform 'helm upgrade' command as shown above,


![image](https://user-images.githubusercontent.com/80065996/150671729-74a7b00b-7c49-435d-b63d-77992b512b3b.png)


![image](https://user-images.githubusercontent.com/80065996/150671747-5fea97e6-8b48-47cd-937e-02c3d4c885f8.png)


# just changed the nodeport value and checked, kubernetes will take only the content given and change it and it will not affect the whole chart installed.


# Danger of using Helm :

# Eventhough Helm is wasy to use and can install any packages within a flash of a second using commands. it comes with its own problems.
# we are not sure what is happening inside the chart which we downloaded from website. moreover if we install any chart on top of cluster we are using
# and if we are planning to move the cluster from baremetal to cloud or any cloud to cloud we will not have YAML, we need to remember the chart we installd manually
# also. installing charts from third party vendors are dangerous and it will change frequently and we have to upgrade it.


# So how can we modify the remote helm chart without installing into our cluster directly
# pull the helm chart using 'helm pull' command


![image](https://user-images.githubusercontent.com/80065996/150737937-cebc9d75-3e15-4972-8bae-cee218b54cef.png)


# this command just downloads the chart and it does not touch my cluster.

# using 'ls' command to check whether it is downloaded the chart correctly


![image](https://user-images.githubusercontent.com/80065996/150738493-62e51319-cf7d-4a54-ad7f-59dfb969ff6f.png)


# This command downloaded the zip file. We need to unzip it to get the YAML file for the stack. 
# Helm pull command with some flag does the job to download the unzipped file for the chart


![image](https://user-images.githubusercontent.com/80065996/150738934-a057aa76-db4a-40f1-a65e-57838105667c.png)


# downloaded the unzipped version


![image](https://user-images.githubusercontent.com/80065996/150739015-e31aa012-ecd0-4cd2-91f8-fc5b401d9d35.png)


# go into the downloaded folder


![image](https://user-images.githubusercontent.com/80065996/150739138-01727832-fdcc-487b-95b8-bca056175491.png)


![image](https://user-images.githubusercontent.com/80065996/150739314-76826c82-e6cf-4003-9f97-0e0c15e2787f.png)


# By downloading this chart, we are having a copy of the chart with us. so in future eventhough from the remote website, if this chart gets deleted
# we can have copy of it and use it for our purpose.

# similaryl download the other charts used in our cluster


![image](https://user-images.githubusercontent.com/80065996/150741073-6737ec09-43be-4737-9495-307c738a40a9.png)


![image](https://user-images.githubusercontent.com/80065996/150741115-ae47e86e-439a-4e86-b0b2-e4d054ebdd38.png)


# now we have 2 charts downloaded and kept,


![image](https://user-images.githubusercontent.com/80065996/150741364-2ccf65ab-1203-48e4-8df9-feaaa15622e3.png)


# helm pull command format := helm pull repo-name/chart-name flags
# repo-name ==> we added using 'helm repo' command
# chartname ==> we take from artfifacthub
# flags ==> there are many flags. we used 'untar flag' to download the unzipped version of the chart


# now we have local copy of charts. We can use 'helm install' command to install the chart using local copy we have


![image](https://user-images.githubusercontent.com/80065996/150742041-241f5b13-0153-4eb0-ab3c-357016ce19d2.png)


# helm install command format := helm install [release-name]  [local-chart-folder-name]


![image](https://user-images.githubusercontent.com/80065996/150742654-6888dcb1-b9ed-44f9-b87a-42fc30bf601c.png)


![image](https://user-images.githubusercontent.com/80065996/150742911-dc0f63e2-b13e-4f04-b469-a2800d443f31.png)


![image](https://user-images.githubusercontent.com/80065996/150742952-c4ac7e92-81ed-4ac6-9272-e6d5732a10e4.png)


