# End-to-End AWS VPC Project

## Overview

This project demonstrates the complete setup of a secure and scalable AWS environment using VPC, EC2, Auto Scaling, load balancing, and best-practice networking and security. The app is deployed in a private subnet and made accessible via an Application Load Balancer.

---

## Architecture Diagram

![Architecture Diagram](images/01-architecture.png)

---

## Step-by-Step Implementation

### 1. VPC and Networking Setup
- Custom VPC, public/private subnets, route tables, and NAT gateways.
- See screenshot:  
  ![VPC Resource Map](images/02-vpc-resource-map.png)

### 2. Auto Scaling Group
- Created an Auto Scaling Group spanning multiple AZs.
- See screenshot:  
  ![Auto Scaling Group](images/03-auto-scaling-group.png)

### 3. EC2 Instances
- EC2 instances launched in private subnets via Auto Scaling.
- See screenshot:  
  ![EC2 Instances Running](images/04-ec2-running.png)

### 4. Bastion Host
- Deployed a bastion host in a public subnet for secure SSH access to private EC2 instances.
- Accessed the private instance and ran a Python web app on port 8000.
- See screenshots:  
  ![Bastion Host EC2](images/05-bastion-host.png)  
  ![Python App Running](images/06-app-port-8000.png)

### 5. Target Group & Load Balancer
- Created target group for the web app (port 8000).
- Set up an Application Load Balancer and attached the target group.
- See screenshots:  
  ![Target Group](images/07-target-group.png)  
  ![Load Balancer](images/08-load-balancer.png)

### 6. Application Access via Load Balancer
- App is accessible from the public internet via the ALB DNS name.
- See screenshot:  
  ![Web App Success](images/09-alb-app.png)

---

## Security Best Practices

- Security Groups and NACLs restrict traffic to only what is needed.
- Bastion host used for SSH access; private keys are securely stored.
- IAM roles and policies restrict instance permissions.

---

## Sample Application

A simple static HTML file (`index.html`) is served using Python's built-in HTTP server on port 8000.

```html
<!-- app/index.html -->
<!DOCTYPE html>
<html>
<body>
<h1>My First aws project to demonstrate app in private subnet</h1>
</body>
</html>
```

**To run the app on your private EC2 instance:**
```sh
python3 -m http.server 8000
```

---

## How to Reproduce

1. Follow the screenshots and steps above in your AWS account.
2. Upload the sample `index.html` to your EC2 instance.
3. Start the HTTP server with:
    ```sh
    python3 -m http.server 8000
    ```
4. Configure your security groups, IAM roles, and route tables as illustrated.

---

## Images

All referenced screenshots are in the `images/` directory.

---

## License

MIT License
