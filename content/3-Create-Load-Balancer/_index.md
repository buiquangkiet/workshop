+++
title = "Create Application Load Balancer"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

- In the Dashboard section, scroll down to Load balancing, select Load Balancer and select **create load balancer**.
![Create Load Balancer](/images/ALBimg/cr-alb.png)
- Select **Application load balancer** and **click create**
![Click Load Balancer](/images/ALBimg/alb.png)
- Name the load balancer
- Select internet-facing

![](/images/ALBimg/configALB.png)

- Select all AZ

![](/images/ALBimg/allAZ.png)

Select default SG and select the newly created target group

![](/images/ALBimg/sg-alb.png)

- After successfully creating ALB

![](/images/ALBimg/done-alb.png)

- To check, copy the **DNS name** of the load balancer in a new tab. If you see the web **change** by almost **50%** after each reload, **congratulations** you have completed the lab.

![](/images/ALBimg/testEC2-1.png)

![](/images/ALBimg/testEC2-2.png)