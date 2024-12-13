+++
title = "Introduction to Application Load Balancing - AWS"
date = "2024-12-11"
weight = 1
chapter = false
+++

# Introduction to Application Load Balancing – AWS

#### Overview
Application Load Balancer (ALB) is a service that provides the ability to distribute application traffic to multiple backend servers to ensure high performance and availability of the application. ALB is a component of the Elastic Load Balancing (ELB) service of Amazon Web Services (AWS).

#### Applications
- Suitable for web applications or APIs that require complex routing capabilities.

- Optimized for microservices architectures thanks to flexible routing capabilities.

- Used in DevOps environments to manage traffic to different service instances.

#### Benefits of using Elastic Load Balancing
- Improve application performance.
- Increase fault tolerance with load balancing and automatic traffic redirection.

- Simplify HTTPS protocol management and security.

#### Lab practice model
![Model](/images/ALBimg/digram.png?width=800)

#### Main content
1. [Create EC2](1-Create-EC2/)
2. [Create Target Group](2-Create-Target-Group/)
3. [Create Load Balancer](3-Create-Load-Balancer/)
4. [Clean-up resources](4-Clean-up-resources/)