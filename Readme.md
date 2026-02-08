# AWS Assignment

## Task 1: Application

- Simple frontend + backend app

- Use one database (MySQL/MongoDB/Influx DB)

- App must connect to the database successfully

## Objective:

This task using docker build a simple application with a frontend and backend that successfully connects to a database (MySQL) to store and retrieve data.

## Steps: 

- Launch one instance and inside instance create following structure:

![](/Images/tree%20structure.jpeg)

- create all directory and file and write code inside the file

-  Write code inside all files and run docker compose file using following command:-

  command:
     
      docker-compose up -d

- Access app using instance public ip

- Fill the form and click Submit

![](/Images/check%20browser%20detail.png)

-frontend successfully connected to backend and data stored in database

![](/Images/added%20record%20in%20browser.png)

- Check record inserted in mysql database


![](/Images/Check%20added%20record.png)

## Conclusion:

The Dockerized application with a frontend, backend, and MySQL database was successfully implemented. The frontend communicates with the backend, and data is stored and retrieved from the database as expected. This demonstrates a simple full-stack application running in containers, making it easy to deploy and manage.

---

## Task 2: Docker
- Create Docker file(s)

- Run app using Docker containers

- Expose required ports

- Ensure containers auto-start on reboot

### Objective:

This task focuses on containerization application using Docker and ensuring deployment,proper port expose and container auto-start on reboot.


## Steps: 
- Launch Ec2 Instance (Ubuntu): SSH to local host and install docker

  command:

         sudo apt update -y

         sudo apt-get install docker.io -y
- Create a dockerfile:

  A dockerfile was created to define the application and dependencies.

![](/Images/Dockerfile.png)

- Build Docker Image:
 
    The Dockerfile was build using Dockerfile.

![](/Images/docker%20build%20file.png)

- Run application using Docker container:
  
  The application was started inside a Docker container using built image.

![](/Images/Docker%20ps.png)

- Expose Required Port:
  
  This allows the application to be accessed from the browser.

![](/Images/Docker%20app%20browser.png)

- Enable Auto-Start on System Reboot:
  
  The container was configured to automatically restart after system reboot


![](/Images/Restart%20policy%20proof.png)

## Conclusion:
   
   This task successfully demonstarte containerization of an application using Docker.

   ---

## Task 3: AWS EC2 Deployment

- Launch EC2 (cost-optimized: t2.micro / t3.micro)

- Install Docker

- Run containers on EC2

### Objective:
Deploy the dockerized application on an AWS EC2 instance using cost-optimized instance type and run the application inside Docker container.

## Steps:

- Launch EC2 Instance:

![](/Images/Ec2%20details.png)

- Connect to EC2 Instance

![](/Images/SSH%20login.png)

- Install Docker on EC2

![](/Images/Docker%20Installation.png)

![](/Images/Docker%20version.png)

- Deploy Application Container on EC2
  
  The Docker image was pulled or built on EC2 and the container was started

![](/Images/nginx%20pull.png)  

- Access Application via Public IP:
  
  The application was accessed using the EC2 Public IP

![](/Images/App%20in%20browser.png)

  Conclusion:
   
   This task demonstrates successfull deployment of a dockerized application on AWS EC2 using cost-effective instance

 ---

## Task 4: Application Access

- Access app via:

- Elastic IP or

- EC2 Public IP

- (Optional) Route 53 domain

## Objective:

Provide secure and reliable access to the deployed application using AWS networking option such as EC2 Public IP, Elastic IP.

## Steps:

- Launch EC2 Instance:
  SSH to LocalHost and inside the instance install nginx 

![](/Images/EC2%20task4.png)

- Access Using EC2 Public IP

![](/Images/browser%20with%20public%20ip.png)

- Access Using Elastic IP
  
  -Allocated Elastic IP from AWS EC2 console
  -Associated Elastic IP with running EC2 instance
  -Verified application accessibility using Elastic IP

![](/Images/Allocate%20ElasticIP.png)

![](/Images/Browser%20with%20ElasticIP.png)


- Access using route 53 Domain

   For a production-like setup, a custom domain was configured using AWS Route 53

- Security Group:
  
  The Security Group was configured yto allow application traffic

![](/Images/SG.png)

## Conclusion:

  This task successfully enables multiple methods for the deployed application,ensuring flexibility,reliability,and production-ready networking using AWS best practice.

  ---

## Task 5: Load Balancer & auto scaling

- Configure Application Load Balancer (ALB)

- Attach Auto Scaling Group (ASG)

- Scale based on CPU utilization

## Objective:

This task focuses on configuring ALB and Auto Scaling to distribute traffic and automatically scale instances based on CPU load.

## Steps:

- Configure Application Load Balancer (ALB)

![](/Images/load%20balancer.jpeg)

- Create Launch template 
  
  A launch template was created to define the instance configuration for the Auto Scaling Group.

![](/Images/task%205%20template.png)

![](/Images/task%205%20temp%202.png)

-  Create Auto Scaling group and attach template

   The ASG manages EC2 instances dynamically based on load, attaching the launch template for configuration.

![](/Images/task%205%20asg.jpeg)

- Scale Up Instances 

   The ASG launched 2 instances initially to handle incoming traffic.

![](/Images/add%20servertask%205.jpeg)

- Scale Down Instances

   When traffic decreases, the ASG automatically terminates one instance to optimize cost.

![](/Images/remove%20server%20task%205.jpeg)

## Conclusion:
This task successfully demonstrates the use of an Application Load Balancer and Auto Scaling Group to manage traffic and dynamically scale EC2 instances based on CPU utilization, ensuring availability and cost-efficiency.


## Task 6: Cost Optimization

- Use free-tier eligible instances

- Minimal resources

- Auto Scaling to avoid over-provisioning

## Objective:
Reduce AWS cost while maintaining required performance.

## Steps:

 - Use Free-Tier Eligible Instances:
   
   Use AWS resources that are included in the free tier

  ![](/Images/ec2%20task6.png)

  ![](/Images/ec2%201%20task6.png)

  - Use Minimal Resources:
    
    Avoid unnecessary resource usage

   ![](/Images/stop%20ec2s.png)

   - Auto Scaling to avoid Over-Provisioning:
    
  Automatically adjust the number of instances based on traffic.

  ![](/Images/template%201.png)

  ![](/Images/template%202.png)
   
  ![](/Images/template%203.png)

![](/Images/running%20template.png)

- Create an auto scaling Group

![](/Images/ASG.png)

-Ensure instances run only when needed reducing cost.

Conclusion:

This project successfully demonstrates cost optimization in AWS by using free-tier eligible EC2 instances and implementing Autoscaling. By scaling instances based on traffic demand.

---

## Task 7: Troubleshooting (Explain) 
- App not accessible

- Container running but port not reachable

- ALB health check failures

## Steps:
 - App not accessible
 
 1. Check EC2 Instance Status:
    
    In EC2 - Instances - ensure system status check and instance status check.
    

 2. Verify Security Group Rules:
    
    Check Inbound Rules - Ensure required ports are open (HTTP:80)
    Source should be: 0.0.0.0/0 (All IP'S)

 3. Check Application Process:
    
    SSH into EC2
    Verify app or container is running or not
  
  - Container running but port not reachable

  1. Verify Port Mapping:

     Check docker port mapping

  2. Check Application Port Inside Container

     -Inside the Container

       cmd: docker exec -it <cont_id>    

     -Verify app is listening on correct port:

       cmd: netstat -tuln  

  3. Verified dockerfile Configuration

     Ensure Dockerfile has correct port 

    Run container using correct port, image name:

        cmd: docker run -p 80:3000 image_name  

- ALB health check failures

  1. Check target group health
     
     Go to target groups - Target

     If status shows Unhealthy, click reason

   2. Verify health Check Path

   3. Verify target Group port

      Ensure target group port matches app port:

        If app run on 3000

        Target group must also use 3000     

    4. Check security group for ALB

  ## Conclusion:

    Application access issues can be resolved by checking EC2 health, security group rules, Docker port mappings, and ALB health check configurations. A systematic troubleshooting approach ensures reliable connectivity and stable application deployment.

       