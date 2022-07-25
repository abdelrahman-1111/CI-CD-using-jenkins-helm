# CI-CD-using-jenkins-helm
## A Brief on project
### I made a CI/CD pipeline using GitHub, jenkins and helm in which the deveopler push thier update on code on Github then i pull this code into my jenkins pipline then as first stage in my pipeline i build this code using Dockerfile then pushing this build (docker image) into my dockerhub repo.
### Now after my image is ready to deploy. i created a chart using helm to create a simple deployment and a service to deploy my app on them and made the templates changeable using variable and the values file to easily use them again in another deployment 
## Implementation
### creating the pipeline 
![Screenshot from 2022-07-24 22-05-44](https://user-images.githubusercontent.com/104630009/180744266-35e510f3-e851-45dc-944b-7e5743b53867.png)
### my jenkinsfile
![image](https://user-images.githubusercontent.com/104630009/180744762-ca4e629d-13d5-42ae-83cb-02bfa438ddb0.png)
- https://github.com/abdelrahman-1111/CI-CD-using-jenkins-helm/blob/master/DevOps-Challenge/jenkinsfile
But i needed to create a credentials to be authorize to push the image to my dockerhub repo so first i generate a token on my dockerhub account then create acredential on jenkins using it
![Screenshot from 2022-07-24 22-15-27](https://user-images.githubusercontent.com/104630009/180745658-23020485-8de4-43f5-bb3b-603345bf3301.png)
### my Dockerfile 
![image](https://user-images.githubusercontent.com/104630009/180745146-27d857da-4582-447f-8ddd-52b478d573a3.png)
- https://github.com/abdelrahman-1111/CI-CD-using-jenkins-helm/blob/master/DevOps-Challenge/Dockerfile 
## Now i will create the helm chart using command `helm create <Chart>` and am gonna modify the created files to match my needs only 
### My deployment template 
![Screenshot from 2022-07-24 22-18-31](https://user-images.githubusercontent.com/104630009/180746358-4f2a6ddc-ae4b-4fd8-8da9-2f200d754f49.png)
### My service template 
- make sure to create Nodeport to be able to access the app from outside the cluster 
![Screenshot from 2022-07-24 22-18-46](https://user-images.githubusercontent.com/104630009/180746418-fbb79466-3195-4546-8508-6a1362310e81.png)
### my values file 
![image](https://user-images.githubusercontent.com/104630009/180746587-663e4e76-b04a-480a-b528-bc74b1225a26.png)
### I modified my chart name and its version and set my app version to be 7.7.7 
![Screenshot from 2022-07-24 22-19-58](https://user-images.githubusercontent.com/104630009/180747958-47d72251-0d6a-4182-9479-33eee06feb5b.png)
### Installing the chart using command `helm install <choose-release-name> /path/to/chart`
![Screenshot from 2022-07-24 22-22-18](https://user-images.githubusercontent.com/104630009/180748009-aa7a0b74-d8aa-4294-8b49-0e5c066cbc63.png)
### check your pods to insure that your containers working correctly 
![Screenshot from 2022-07-24 22-22-45](https://user-images.githubusercontent.com/104630009/180748116-5ac5aefd-daea-48e3-901e-41c9247a47bd.png)
### get my node ip to access it on my browser using command `kubectl get node -o wide` 
![Screenshot from 2022-07-25 11-48-32](https://user-images.githubusercontent.com/104630009/180749323-41d8829c-193e-4ea9-bf54-92a2125b5d5d.png)
### now open the ineternal node ip on port 30007 `as i set on my service nodeport`
![Screenshot from 2022-07-24 22-25-10](https://user-images.githubusercontent.com/104630009/180750017-380ea248-5f79-45c9-bddc-3a4eb42ac8f1.png)
