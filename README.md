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


# Now we have local copy of 'values.yaml' now. Good practise is not to alter that 'values.yaml' file. because after sometime if some updates happend to 
# the chart, there will be change in contents of 'values.yaml'. so our changes done to 'values.yaml' in local copy will get overrided which downloading the 
# copy of new version.
# so always keep the separate file with values needed for overriding the main 'values.yaml' file. so that any change in the 'values.yaml' in the future will not 
# get impacted.


![image](https://user-images.githubusercontent.com/80065996/150750759-e1d2d49c-ab9f-4137-ac55-581e3da6bc65.png)


![image](https://user-images.githubusercontent.com/80065996/150750910-b8a0f683-4bbe-4642-838c-3bab211cb82c.png)


![image](https://user-images.githubusercontent.com/80065996/150750963-7c300488-cdfd-4b84-b8c0-e870fc63c6fe.png)


![image](https://user-images.githubusercontent.com/80065996/150751279-51891338-d0c2-4b98-a193-6d9b4456d3c8.png)


![image](https://user-images.githubusercontent.com/80065996/150751541-1ffe6d5d-4069-498b-b74a-a3d30b7807f8.png)


# so we got separate new file for overriding purpose,
# so when a chart is running already and you want to use this overriding file, we can apply that using below command,


![image](https://user-images.githubusercontent.com/80065996/150752923-64413156-239d-4f40-93dc-16aad6f7b557.png)


# dont fogot to use dot (.) operator at the last.
# so the new override file will be applied. so even if you upgrade this chart in future, we will not distrub the orinal 'values.yaml' file and use this 
# override file 'myvalues.yaml' to configure the charts.


# Generating YAML using HELM.
# why do we need to do this ? := one downside of using HELM is we always have HELM installed on top of our running cluster. Our kubernetes cluster, we will create
# anyhow by scripting YAML files. But since we are using third party charts, we need to have HELM installed.
# How to avoid this dependency ? := some projects will not use HELM to install charts, instead they will use HELM to generate YAML file so that we can use the 
# YAML for our purpose.


![image](https://user-images.githubusercontent.com/80065996/150754684-96bf0af2-7e88-4d2f-b90f-21d7b400c348.png)


# command from above image generate YAML file from the local copy of chart we downloaded along with override we applied using 'myvalues.yaml'. ('monitoring' is the
# release name we used to identify this.
# but the problem is it will put the whole yaml in the screeen which is not good. we have to copy it and use it for our purpose.


![image](https://user-images.githubusercontent.com/80065996/150756854-fa154d65-720b-4c3b-b90a-ded55c41424c.png)


# so we use linux command feauture to copy the output to a separate YAML file (monitoring.yaml)


![image](https://user-images.githubusercontent.com/80065996/150757944-a8001459-e5b7-414b-84a1-e74278f5b160.png)


![image](https://user-images.githubusercontent.com/80065996/150758015-daedf96f-89a6-4e7d-bdab-63420d6084b4.png)


# One advantage is this is just a normal YAML file we can use 'kubectl apply -f' command to install into the cluster.
# one Drawback is 'monitoring.yaml' file we created has more than 15000 lines to work which is very tedious job.


# creating GO templates for helm charts - (creating and using our own helm charts).


![image](https://user-images.githubusercontent.com/80065996/150765872-c1705ead-489e-4413-80a5-23bd7fd456b6.png)


![image](https://user-images.githubusercontent.com/80065996/150765990-94903da5-d458-411b-b2cb-2e440319c87c.png)


![image](https://user-images.githubusercontent.com/80065996/150766124-37be7584-0dfe-45a4-bd7f-58ab5d7ccded.png)


**Open the folder in atom,**


![image](https://user-images.githubusercontent.com/80065996/150786981-db84ff26-630b-4ca0-ae65-3d00502ab61c.png)


**below highlighted are default files created if we use 'helm create' command,**


![image](https://user-images.githubusercontent.com/80065996/150787168-066df928-a21f-4f8e-a4f2-efbe587179f7.png)


**so deleting the files,**

# charts.YAML is the file which provides information about that chart. this is like READ.ME file in git


![image](https://user-images.githubusercontent.com/80065996/150787480-661c90c8-4144-489a-8971-d26bc10f12f4.png)


# under templates folder, create a file called 'one.yaml',


![image](https://user-images.githubusercontent.com/80065996/150788576-c39d1ca0-d68e-4e0d-9b70-2b3feaeec51a.png)


# Thats all, we have got a basic set up of our own helm chart,


![image](https://user-images.githubusercontent.com/80065996/150790124-34d683d3-a9c0-470c-a23b-114542d2b352.png)



# 'values.yaml' file contains default values for this chart.


# below are default set up. we can run 'helm template .' command so that it will pass the content of yaml files inside the chart and check for errors,


![image](https://user-images.githubusercontent.com/80065996/150791252-b7eb2f47-2d1c-4886-9037-3ef4fef88f2e.png)


# deliberately doing the issue in YAML,


![image](https://user-images.githubusercontent.com/80065996/150791418-23f9e3fe-b960-498e-a066-cc07501b042b.png)


![image](https://user-images.githubusercontent.com/80065996/150791507-55e671b6-9987-4efb-86fd-0c111602558a.png)


# it is successfully validating the YAML file for wrong values as well


# WRITING GO TEMPLATES FOR HELM CHART


![image](https://user-images.githubusercontent.com/80065996/150792876-59e5be30-938e-451b-a593-4a47058a2d72.png)


# JUST introduced a 'printf' statement for golang,  and if you have 'helm template .' inside the chart folder, it will vaidate the yaml and execute it


![image](https://user-images.githubusercontent.com/80065996/150793525-728d2332-0328-4128-b9b7-32d7a373743c.png)


# trying again with some other value,


![image](https://user-images.githubusercontent.com/80065996/150795883-8e39fbfc-3159-42d8-a3be-21e505243f2e.png)


![image](https://user-images.githubusercontent.com/80065996/150795958-b52840e4-887d-416c-a671-4f7fb229384e.png)


# lets be more realistic in creating example with GOLANG template which makes dynamic 


![image](https://user-images.githubusercontent.com/80065996/150800748-022a945b-cdcc-4b7f-9f22-97c468dac848.png)


**delete the unnecessary files, and create a new file and putting contents of fleetman-webapp deployment and services.**


![image](https://user-images.githubusercontent.com/80065996/150801467-80012cf1-56d9-4812-ac64-d845021095cc.png)


# now run the 'helm template .' command to check for any errors,


![image](https://user-images.githubusercontent.com/80065996/150804584-a861f2cd-1923-4cee-a0ad-8af88a364752.png)


![image](https://user-images.githubusercontent.com/80065996/150804647-11062571-d5bb-4fff-8fa7-69d808f0c5f3.png)


# there are no errors YAML looks good

**empty the values.Yaml file**


![image](https://user-images.githubusercontent.com/80065996/150806280-658f9879-13f4-40aa-945f-09f9b2be6174.png)


now we can make that fleetman webapp deployment yaml as very dynamic. let starts with replicas,

# step:1
**In 'values.yaml' mention the properties of replicas as shown below,**


![image](https://user-images.githubusercontent.com/80065996/150807355-870eced5-acbf-4f4f-a8cc-bfff216a7e38.png)


# step:2 
# use the placeholder in values.yaml file and code it in deployment of fleetman webapp to replace the value of replicas as shown below


![image](https://user-images.githubusercontent.com/80065996/150808341-25720957-02be-4db6-8f83-1ccb7906d640.png)


# another way to do it


![image](https://user-images.githubusercontent.com/80065996/150809754-0f8cba36-0d74-45cd-bab3-21c02d76d35d.png)


![image](https://user-images.githubusercontent.com/80065996/150809883-13a5f08b-ca1a-41d6-9a13-e98c61d372ea.png)


# check 'helm template' to check for any errors,


![image](https://user-images.githubusercontent.com/80065996/150810159-bcb14bd8-1862-423f-a4fe-977380a6db23.png)


# we can also use set command to do this

![image](https://user-images.githubusercontent.com/80065996/150810777-59393b09-a1f4-40c2-b009-965e5e656516.png)


![image](https://user-images.githubusercontent.com/80065996/150821882-453525df-aa6a-4ee8-8ec4-63eaa5a677c8.png)


![image](https://user-images.githubusercontent.com/80065996/150821963-8f049f6f-22b8-4f17-8b97-02c56ddb74a1.png)


![image](https://user-images.githubusercontent.com/80065996/150822095-b473490f-aeee-46a3-b349-c569b1cb9eeb.png)


Placeholder replaced successfully,


![image](https://user-images.githubusercontent.com/80065996/150822211-840328e4-901b-4807-a216-461f30b29d1e.png)


# Problem: Since we are using placeholders, we can even override that with wrong names. We have to avoid that problem.


Changed some random alphabhets to uppercase in values.yaml file


![image](https://user-images.githubusercontent.com/80065996/151315324-1b0ec8ce-742d-4b29-a93d-a7fc3e32511a.png)


![image](https://user-images.githubusercontent.com/80065996/151315854-a4874e25-e57d-4970-bcb8-2dfbe8b51742.png)


![image](https://user-images.githubusercontent.com/80065996/151315915-26a83a5e-32f0-4d2c-a728-fee4e36184ca.png)


we can avoid this,

# Solution : Helm functions and pipelines


we can use a golang functions to make the name into complete lower case,


![image](https://user-images.githubusercontent.com/80065996/151316239-b3235073-40c3-4cce-aea0-05ea3edd2622.png)


![image](https://user-images.githubusercontent.com/80065996/151316307-1de8e005-4299-46e3-842d-82395be732e6.png)


![image](https://user-images.githubusercontent.com/80065996/151316353-e76a30cd-caa4-48e3-b5e0-2330b88ba797.png)


Lets try upper function too,


![image](https://user-images.githubusercontent.com/80065996/151316484-6e70cb19-e23f-4f4c-88ab-886ab4543f23.png)


![image](https://user-images.githubusercontent.com/80065996/151316554-1265ce3d-2796-4e42-9880-678cb0bbb7fe.png)


![image](https://user-images.githubusercontent.com/80065996/151316630-064636f6-ce18-440e-a266-c434bfbc7758.png)


# problem 2: what will happen if we dont have value of the placeholder not available in 'values.yaml'


removing the placeholder from 'values.yaml'


![image](https://user-images.githubusercontent.com/80065996/151318197-5b0075d6-3946-4e62-8c40-d66295203963.png)


![image](https://user-images.githubusercontent.com/80065996/151318570-f16a8bac-2121-4705-af77-ce9b0d44260f.png)


![image](https://user-images.githubusercontent.com/80065996/151318696-2a3aac9a-b389-438e-bd03-b69280f577e2.png)


# 'helm template .' command throws error if we dont have values mentioned for corresponding placeholder in 'values.yaml'


![image](https://user-images.githubusercontent.com/80065996/151319258-7e25061c-ca26-4408-aef6-36e15eb67f63.png)



![image](https://user-images.githubusercontent.com/80065996/151319657-968883a9-8354-45ed-9939-5dbc63d48919.png)



![image](https://user-images.githubusercontent.com/80065996/151319836-117b7a73-b5b9-47a9-9440-9bac171583c8.png)


![image](https://user-images.githubusercontent.com/80065996/151319872-293e8015-3fe5-494d-8d9e-367b91df1509.png)


# helm pipeline syntax: we can have output of one function to be passed to input of another function using 'pipe(|)' symbol


![image](https://user-images.githubusercontent.com/80065996/151320588-a84e2de2-d346-454c-94b1-3f58054221d2.png)


![image](https://user-images.githubusercontent.com/80065996/151320771-622d3a0f-1982-4785-a599-9e86a5b6ce08.png)


![image](https://user-images.githubusercontent.com/80065996/151320852-3a647681-17f1-4e62-b6b8-4428afedf651.png)


![image](https://user-images.githubusercontent.com/80065996/151320886-42ebd733-7498-447c-8d8c-be94cb14420c.png)


# we can combine multiple values using pipeline


![image](https://user-images.githubusercontent.com/80065996/151321269-35f41192-4f34-4ea4-a5e4-6065e8b7d196.png)


![image](https://user-images.githubusercontent.com/80065996/151321463-c8594231-94da-4a23-8797-afc8292320e5.png)


![image](https://user-images.githubusercontent.com/80065996/151321494-7ac1f41e-2e0b-4f6c-acc3-5687e27502ce.png)


# separating production and development with a single line of change.

# introduce a new field called 'environment' in 'values.yaml' file


![image](https://user-images.githubusercontent.com/80065996/151323615-4101e4c0-ac4f-449b-8297-4a710945908a.png)


![image](https://user-images.githubusercontent.com/80065996/151323715-6c0cdf74-2ded-45f2-8267-1337a12cf6fd.png)


![image](https://user-images.githubusercontent.com/80065996/151323780-8cb9ee56-3089-4ec6-a667-a07e501a52b0.png)


![image](https://user-images.githubusercontent.com/80065996/151323843-50417819-f192-447a-924c-899386b77d8b.png)


another way to handle this,


![image](https://user-images.githubusercontent.com/80065996/151333051-321c19b0-cd56-4bd3-aecc-6674958a09ec.png)


![image](https://user-images.githubusercontent.com/80065996/151333258-7facf0cb-c3f1-43a6-8e3f-60fe4e7faa21.png)


another different way to handle this,


![image](https://user-images.githubusercontent.com/80065996/151333398-dc94bd63-1c06-4aed-a28f-e1e372fe3c34.png)


![image](https://user-images.githubusercontent.com/80065996/151333690-559306e0-9468-469a-8093-c40b1a2e4087.png)


![image](https://user-images.githubusercontent.com/80065996/151333773-8d293282-c03b-485b-a0bf-61f92d780b63.png)


![image](https://user-images.githubusercontent.com/80065996/151333826-e0e6cb25-e422-486d-9e75-a969424eaa9d.png)


# making it as values other than 'true'. put some random values


![image](https://user-images.githubusercontent.com/80065996/151334802-b0164a21-fad3-44da-b698-131319d34f55.png)


![image](https://user-images.githubusercontent.com/80065996/151334875-ea9132cf-4b39-4f79-b299-13b04cc215a7.png)


# giving strings or anyother value apart from boolen throws incompatible type error.(since its golang code it will be strongly typed)


# Another way to do it,


![image](https://user-images.githubusercontent.com/80065996/151335597-80fa6076-ab2e-4f41-a898-1fa72a2f553d.png)


# check for boolean


![image](https://user-images.githubusercontent.com/80065996/151335850-eeff9165-97aa-46e8-852b-ac3703cc9ce5.png)


# if else block


![image](https://user-images.githubusercontent.com/80065996/151336145-5e4e8e45-af3d-4e0c-a5d5-40ceead47715.png)


# 'true' scenario


![image](https://user-images.githubusercontent.com/80065996/151336253-89e2de23-e9d4-4125-b42e-3075d8284c72.png)


![image](https://user-images.githubusercontent.com/80065996/151336287-ce12f8a3-8e9f-4971-9f2c-b4cf1e49263b.png)


![image](https://user-images.githubusercontent.com/80065996/151336334-6301d5d5-1d45-4641-b70a-14d9961188b9.png)


# 'False' scenario


![image](https://user-images.githubusercontent.com/80065996/151336402-46bdca76-2e61-4660-b79d-c4d90e484f4e.png)


![image](https://user-images.githubusercontent.com/80065996/151336474-f8b63831-ca0c-40ae-8e58-8f8055a561da.png)


![image](https://user-images.githubusercontent.com/80065996/151336531-7515f967-8f57-4951-8d02-611bb4c67fc3.png)


# Named Templates - sub charts


# problem: till now we have used 'values.yaml' to replace only a single value. What if we want to use a entire YAML file inside the another YAML (template
# we are creating now for our use. we have to use different construct for that. that is called sub charts)


# suppose below highlighted image we are supposed to use in many places in our YAML file.so this block of code will be repetitive. so for this case,
# we can use named templates.

# removed the particular block of code like shown below,


![image](https://user-images.githubusercontent.com/80065996/151338196-eb0449be-3e39-4353-811b-525eb20e136f.png)


# create a new file called 'common-block.yaml' under 'templates' folder,


![image](https://user-images.githubusercontent.com/80065996/151338770-d2cffc0e-bd59-4bfe-857e-e8458ba4c31e.png)


# what helm does is, it will take each and every yaml file under 'templates' section and check for syntax errors and does 'kubectl apply' command to it while
# running the chart. we dont want to do with this 'named template' we are creating. Because this is the common block of code we want to replace the main YAML
# and it has to called from main.YAML file similar to regular function call instead of applying it as separate entity.


![image](https://user-images.githubusercontent.com/80065996/151339217-013a711d-3cff-440d-a63e-52d55946962b.png)


# now if we do 'helm template .'  for checking the syntax, it consider this 'common-block.yaml' file as separate entity rather than calling it from main YAML file
# and throws error as highlighted below


![image](https://user-images.githubusercontent.com/80065996/151339557-c4a6c6b8-a78a-46fe-abec-543080c99845.png)


# debug the template content using '--debug' flag as shown below,


![image](https://user-images.githubusercontent.com/80065996/151339969-61ae3c9c-4b05-4336-b1a7-cedc65b1c77e.png)


# if you see the debug trace it generated, helm is trying to consider this 'common-block.yaml' file as separate entity rather than replacing as function call
# from main yaml file.


![image](https://user-images.githubusercontent.com/80065996/151340439-bceba62b-fb80-46f5-8661-a5fbba84cdad.png)


# USE UNDERSCORE SYMBOL ( _ ) TO TELL THE HELM COMPILER TO IGNORE THAT PARTICULAR YAML FILE FROM COMPILING, BUILDING AND ALSO TELLING HELM TO AVOID CHECK ERRORS

# RENAME THE FILE NOW,


![image](https://user-images.githubusercontent.com/80065996/151340970-4788e0b6-d7a4-4f86-b289-1432e3e9aaa9.png)


![image](https://user-images.githubusercontent.com/80065996/151341034-af30b11c-afbb-4082-a28c-c927b224f41f.png)


![image](https://user-images.githubusercontent.com/80065996/151341262-48cb9cbc-ca2f-4dd3-bc29-ad3a6de1be7e.png)


# if you see now it didnt throw error, as it skipped compiling and build file starts with underscore


![image](https://user-images.githubusercontent.com/80065996/151341426-a8a670a5-3710-498e-8018-e8be2eb6c11f.png)


![image](https://user-images.githubusercontent.com/80065996/151341485-3370aabd-5592-41fb-8b56-e4543ffc9ae1.png)


# ALSO TRY USING THE EXTENSION OF '.TPL' WHEN YOU ARE CREATING THIS KIND OF FILE.


![image](https://user-images.githubusercontent.com/80065996/151341777-bea821bf-1b7c-4487-ab16-a0335a4b9794.png)


![image](https://user-images.githubusercontent.com/80065996/151341974-d6fb6261-111d-440d-9976-c11f49ecad0f.png)


# another step to make the helm to understand the particulat YAML file as template file.
# we have use keyword 'define' to create a new function.


![image](https://user-images.githubusercontent.com/80065996/151342941-f9a77f1c-7aad-46a0-9151-071e0faf2ce0.png)


# like below syntax, we can connect the function defined in 'common-block.tpl' file with our main YAML file,


![image](https://user-images.githubusercontent.com/80065996/151343426-c5fe263b-dc9f-43d9-a386-9502400af95a.png)


![image](https://user-images.githubusercontent.com/80065996/151343510-d9d1f3f6-1815-46c9-bade-e1986b67b388.png)


![image](https://user-images.githubusercontent.com/80065996/151343565-d57b71a7-5569-405f-bfb2-c5f7cdeee401.png)


# we have successfully connected the 'common-block.tpl' file with our main YAML file as shown above
# Another thing to notice here is even it executed the placeholder values we defined in 'values.yaml' file. 


![image](https://user-images.githubusercontent.com/80065996/151343900-144eb5c8-c2c6-49ab-9fc8-1362d9adf4ef.png)


![image](https://user-images.githubusercontent.com/80065996/151343944-7b672b45-0726-4cb7-93e1-d1786d746305.png)


# we can even check that by replacing values of 'values.yaml' file by using command 


![image](https://user-images.githubusercontent.com/80065996/151344197-7ba03146-5875-42b3-b5a2-89ea70011a02.png)


![image](https://user-images.githubusercontent.com/80065996/151344286-f3ec3ceb-25e3-469f-b59f-f3ce858e5905.png)


# it bring in the template as well as pipeline operations executed and also it fetches value from 'values.yaml' and it can even take values from command line
# and replaces the values.yaml properties and sync it with our main YAML file

# there is a blank line always got created when we use go action (double braces), because every go action executed and creates a blank line. To avoid that
# we have to use hyphen(-) to remove the white space.


![image](https://user-images.githubusercontent.com/80065996/151350231-e96ebc8f-e010-423c-b885-6330a70416e6.png)


![image](https://user-images.githubusercontent.com/80065996/151350363-44e5d953-aadb-44f4-8021-1d8a6d437788.png)


# now could see no new space created,


![image](https://user-images.githubusercontent.com/80065996/151350434-c7623081-efd8-44ce-b100-c2b31f85136d.png)


# problem : indendation in yaml. we should not hard code any spaces in the common-block.tpl kind of template files.

# below highlighted kind of spaces we should not use in 'common-block.tpl' file because we are really not sure on which place of the main YAML file we are going 
# to replace this common content. So we cannot really hardcode the indendation. there is another way to do it.

# step 1: Remove the unwanted indendation and make the file to look like below,


![image](https://user-images.githubusercontent.com/80065996/151353921-ad2d6367-2200-41a0-8db9-7d90dd7b818e.png)


# step 2: problem : now if you test this with 'helm template .' command it will show error for indendation.


![image](https://user-images.githubusercontent.com/80065996/151354230-56792182-fc00-4776-a8c1-599c13248cd1.png)


# step 3: check the yaml using "--debug" flag. it is clearly showing the common-block.tpl content replaced the placeholder without any spaces and it throwed error


![image](https://user-images.githubusercontent.com/80065996/151354552-eb54ed46-b411-412d-9a84-819ba1057b48.png)


# step 4: Solution: Dont try to move the the placeholder left or write. we can mention the placeholder in any position. it does not matter. Even if we to any position
# the content we are replacing with that placeholder will not get indended with any spaces.
# demo: putting the placeholder in extreme right side


![image](https://user-images.githubusercontent.com/80065996/151355141-dfc5faca-f6d9-4cd9-b230-39a4ac4afb06.png)


![image](https://user-images.githubusercontent.com/80065996/151355235-d46423d2-47cb-40ab-abba-592c2d68aa18.png)


# still the same result. indendation will not changed. checked using '--debug' flag


# step 5: use below syntax to make indent of 6 spaces.


![image](https://user-images.githubusercontent.com/80065996/151357561-8fd67d57-fcbb-4c12-9e09-f8b237fb6c56.png)


# but still we could see error. This is where real differences comes into play for command 'templates' and equivalent command 'include'


![image](https://user-images.githubusercontent.com/80065996/151358394-f5a7009a-377d-4535-9ca7-91418595bb86.png)


# step 6 : solution: use 'include' command intead of 'template' command 
# always use 'include' command in your template files(.tpl) files. even if you see 'template' command in any pre coded yaml files, replace it with 'include' command


![image](https://user-images.githubusercontent.com/80065996/151358983-1b6dd646-5b27-4fa6-ac5d-232eb072433f.png)


# now check the syntax,

![image](https://user-images.githubusercontent.com/80065996/151359073-7853fa23-d9ef-41e0-b8a0-a0d885026c53.png)


![image](https://user-images.githubusercontent.com/80065996/151359133-161d1205-4208-4e3a-82a6-134bbe6d2d13.png)


# Take away : we should not use any spaces in template files (here- common-block.tpl) files. we have to always use 'include' instead of 'template'
# use the syntax of 'indent' with 6 spaces always to make the 'named template' fit correctly with main yaml file


# Analysig the existings professional helm charts


![image](https://user-images.githubusercontent.com/80065996/151362706-01771141-52aa-4953-a0de-a1dd2fb27d11.png)


# we have installed the helm chart we have created. 


![image](https://user-images.githubusercontent.com/80065996/151363126-48e4d29a-adda-4487-a676-014284397b7d.png)


# changed the replicas and upgrade the helm 


![image](https://user-images.githubusercontent.com/80065996/151363656-6288195e-6739-43dd-986a-6c1eaef13149.png)


![image](https://user-images.githubusercontent.com/80065996/151363922-992a7e81-29d1-4ee1-b353-eefe4bfec79e.png)


![image](https://user-images.githubusercontent.com/80065996/151363970-a9130c5a-a1fb-4a12-afc4-2a33063febcf.png)


#  till now we installed TEST version. now you can see with single command i am going to switch to PROD


![image](https://user-images.githubusercontent.com/80065996/151364461-549b2590-fa4f-4336-ae59-869338039ec8.png)


# since i changed 'set flag development=false from true' it now switch the chart to production version from TEST version


![image](https://user-images.githubusercontent.com/80065996/151364595-0a054e69-a3b2-4223-9484-b70367a9d0bf.png)


![image](https://user-images.githubusercontent.com/80065996/151372136-6373164e-3f46-4004-90d6-c776b382bea6.png)


# here you could see name of helm release is not prefixed with any of the pods,deployments,services,replica sets. so in case of bigger clusters, this
# will create confusion. so we need to code separately for this to happen,


![image](https://user-images.githubusercontent.com/80065996/151375509-8d81f72d-4d3b-41a1-ab0f-b442eb9b6e20.png)


# we have mentioned separatley the name of deployment,services with placeholder below,


![image](https://user-images.githubusercontent.com/80065996/151376211-dcdafc50-37c1-4e4a-9318-35f4171c2ff8.png)


![image](https://user-images.githubusercontent.com/80065996/151376379-2947ad05-2b79-4e20-b0ab-f62e51aa048d.png)


# now as per our changes release name is appearing on every kubernetes object


# Note: We can install same chart twice using different release name with two install command with same code we have developed.


![image](https://user-images.githubusercontent.com/80065996/151377939-cf23bbdc-adcb-4380-b90c-9773ca3fb5d3.png)


