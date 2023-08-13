# CLO835---Final-Project-Group-10

Flow I have Used:

docker build -t my_db -f Dockerfile_mysql . 

docker build -t webapp -f Dockerfile . 

docker run -d -e MYSQL_ROOT_PASSWORD=pw  my_db

docker ps

export DBHOST=172.17.0.2
export DBPORT=3306
export DBUSER=root
export DATABASE=employees
export DBPWD=pw
export APP_COLOR=blue

docker run -p 81:81  -e DBHOST=$DBHOST -e DBPORT=$DBPORT -e  DBUSER=$DBUSER -e DBPWD=$DBPWD  webapp

curl localhost: 81

Updated Security Group of EC2 instance to allow Port 81

Browsed the IP address of EC2: IP: 81

Created a ECR repository

Pushed the image using workflow

updated AWS credentials file

installed kind

created a new iam policy to allow eks to list and read the image file of s3

did the prequisite for eks installation

created a cluster using eks-config yaml file

executed the below cmnd for  ODIC role for s3
eksctl utils associate-iam-oidc-provider --region=us-east-1 --cluster=clo835 --approve 

created a namesapce in kubectl 'final'

eksctl create iamserviceaccount --name clo835 --namespace final --cluster clo835 --attach-policy-arn arn:aws:iam::547747823946:policy/S3-IAMpolicy --approve

executed the manifest files in belo order
serviceaccount
config
mysecret
pvc
pv
sqldeployment
sqlservice
appdeployment
appservice
