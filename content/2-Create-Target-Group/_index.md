+++
title = "Target Group"
date = 2021
weight = 1
chapter = false
pre = "<b>2. </b>"
+++

- In the Dashboard section, pull down Load balancing and select Target group

![](/images/ALBimg/tg.png)

- Select **Create Target group**

![](/images/ALBimg/cre-tg.png)

- Select Target type: **Instance**

![](/images/ALBimg/instance-tg.png)

- Name the **target group**

- Name the target group
- Select HTTP method and port 80
- IP address type is IPV4
- Click **Next**

![](/images/ALBimg/name-tg.png)

- Select the instances you want to associate with the target group
- Click **Include as pending below**

![](/images/ALBimg/allinstance.png)

- Click **Create target group**

![](/images/ALBimg/click-create-tg.png)

- Target group after successful creation

![](/images/ALBimg/done-tg.png)