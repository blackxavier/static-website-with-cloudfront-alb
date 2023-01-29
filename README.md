# How to setup CloudFront with Application Load Balancer.


![Content delivery using Cloudfront and ALB. ](https://github.com/blackxavier/static-website-with-cloudfront-alb/blob/main/alb-cloudfront.drawio.png "Infrastructure image ")


## Prerequisite

1. Create a security group for the ALB
2. Create a security group for you EC2 servers

## Steps


1. Create a launch template with preferred configuration (Use your previously created EC2 security group here). 
2. Create an auto-scaling group, while doing this create a load balancer and a target group. Use you previously created launch template. 
3. Edit your EC2 security group and allow HTTP and HTTPS traffic from the ALB security group
4. Edit your ALB security group to allow HTTP and HTTPS traffic from the world (0.0.0.0/0), and allow outbound HTTP and HTTPS to yur EC2 security group only.
5. Create a cloudfront distribution. 
6. The origin should be your recently created ALB
7. Modify the following settings, the remaining settings can remain default. 

  ``` 
      Protocol - HTTPS ONLY
      Viewer protocol policy -redirect HTTP to HTTPS
  ```
6. Create distribution. 
7. It would take a couple minutes to propagate. 
