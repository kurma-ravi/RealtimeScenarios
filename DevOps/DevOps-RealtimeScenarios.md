# DevOps RealTime Scenarios

## How to copy files on to a Docker Container ?
	The file has to be on the Docker Server. To copy this file on to the running container, run the below command.
		`docker cp <filename> <containerID>:/tmp/`
    Now, to check the file is copied on the container or not, run below commands
		`docker exec -it <containerID> bash`
		`cd /tmp`
	NOTE: You can also copy the files to docker container using DockerFile.

## How to login to docker container and run commands ?
	`docker pull tomcat:latest`
	/* The below command will run tomcat container in detached moded. Best practice instead of "-it" mode*/
	`docker run -d --name webserver tomcat`
	/*Connecting to running container & run your commands */
	`docker exec -it <containerID> /bin/bash`
	
##  S3 as a artifact for Jenkins

### Prerequisites
1. Create Jenkins Server
  Jenkins server

   ### Setup steps 
1. Create a S3 bucket to store artifacts  
    `S3 --> Create bucket `
      ```sh 
   Bucket name: valaxy-s3-artifact 
   Region: Singapore
   ```
1. Create new IAM role with "S3 full access" and assign it to jenkins server  
   `IAM --> Create role --> EC2` 
   ```ssh 
   Permission: AmazonS3FullAccess 
   Tags: key - Name, Value - S3FullAccess Role 
   name: S3_Full_Access
   ```
   
1. Install "S3 Publisher" plugin on Jenkins  
  `Manage Jenkins --> Manage Plugins --> Availabe --> S3 publisher`

1. Configure S3 profile on Jenkins  
  `Manage Jenkins --> Configure Systems --> Amazon S3 profiles` 
   ```sh
   Profile name : s3-artifact-repository 
   Use IAM Role : chose
   ```