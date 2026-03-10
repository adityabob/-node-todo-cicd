Docker to AWS Deployment | ECS + ECR Real-World Project


step1 : create an ec2 intance ->ubuntu-> t2 micro-> with a key pair ->launch instance

step2: connect ec2 intance through terminal in your local device

step3: now you can update system using -> sudo apt install

step4: clone the repository using git clone command --> git clone https://github.com/LondheShubham153/node-todo-cicd.git

step 4 : remove  DevSecOps/ terraform/  azure-pipelines.yml kustomize/ directories from the project

step 5: AWS ->ECR->create public repo -> give name-> todo-app -> select os -> linux--> processor all check

step 6: go to  node-app repo -> click view push commands

step7: create iam user-> give iam full access->give ecr-ecs permissions and go in security permissions and create access tokens



step8: go to terminal  install docker and amazon cli
      -> sudo apt install docker.io
      -add user to docker group to access docker group
      -> sudo usermod -aG docker ubuntu
      now reboot the system
      -> sudo reboot

      -> aws configure
      and paste copied access tokens from user
   
      now install aws cli using aws documentation online
      
step9: open view push notification and follow the docker authentication steps in ecr
step10: go  to terminal and get inside project directory
 -> cd node-todo-app
 -> docker build -t node-app .
 -> docker tag node-app:latest public.ecr.aws/g2l2u7w2/node-app:latest
 -> docker push public.ecr.aws/g2l2u7w2/node-app:latest
step 11: go to ecr you can see the image is pushed and available in images of node-app
 now in ecs->create cluster-> select fargate->enable insights for cloudwatch -> create cluster

 step12: now in ecs go in task defination 
   -> create task defination and select deploy  and run task

   you can see  in ecs ->tasks ->application status is running

   step 13:click on task and copy public ip:8000  and paste it into web browser now you can see we have deployed the app (make sure that your that security group port no 8000 is open)

   you can also access logs through cloudwatch
      
