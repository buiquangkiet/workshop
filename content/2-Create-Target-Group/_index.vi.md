+++
title = "Target Group"
date = 2021
weight = 1
chapter = false
pre = "<b>2. </b>"
+++

- Ở phần Dashboard kéo xuống Load balancing chọn Target group
![](/images/ALBimg/tg.png)

- Chọn **Create Target group**

![](/images/ALBimg/cre-tg.png)

- Chọn Target type: **Instance**

![](/images/ALBimg/instance-tg.png)

- Đặt tên cho **target group** 
- Đặt tên cho target group      
- Chọn phương thức HTTP và port 80        
- IP address type là IPV4   
- Click **Next**  

![](/images/ALBimg/name-tg.png)

- Chọn các instances bạn muốn liên kết với target group
- Click **Include as pending below**

![](/images/ALBimg/allinstance.png)

- Click **Create target group** 

![](/images/ALBimg/click-create-tg.png)

- Target group sau khi tạo thành công

![](/images/ALBimg/done-tg.png)