+++
title = "Tạo Application Load Balancer"
date = 2021
weight = 3
chapter = false
pre = "<b>3. </b>"
+++

- Ở phần Dashboard kéo xuống Load balancing chọn Load Balancer và chọn **create load balancer**.
![Create Load Balancer](/images/ALBimg/cr-alb.png)
- Chọn **Application load balancer** và **click create**
![Click Load Balancer](/images/ALBimg/alb.png)
- Đặt tên cho load balancer     
- Chọn internet-facing

![](/images/ALBimg/configALB.png)

- Chọn tất cả AZ

![](/images/ALBimg/allAZ.png)

Chọn default SG và chọn target group vừa tạo

![](/images/ALBimg/sg-alb.png)

- Sau Khi tạo ALB thành công

![](/images/ALBimg/done-alb.png)

-Để kiểm tra, bạn hãy copy **DNS name** của load balancer trong tab mới. nếu bạn thấy web **có sự thay đổi** theo tỉ lệ gần như **50%** sau mỗi lần reload thì **xin chúc mừng** bạn đã hoàng thành bài lab.

![](/images/ALBimg/testEC2-1.png)

![](/images/ALBimg/testEC2-2.png)