+++
title = "Tạo EC2"
date = 2021
weight = 1
chapter = false
pre = "<b>1. </b>"
+++

> **Ghi chú:** Chúng ta sẽ dùng default VPC và Subnet để tạo nhanh EC2  

- Truy cập **AWS Management Console:**
  - Điều hướng đến EC2      
  - Nhấp vào Instances 

![AWS Management Console](https://000003.awsstudygroup.com/images/4-CreateEc2Server-update/1-Create-EC2-Server/EC2-img1.png?featherlight=false&width=60pc)

- Click vào **Launch Instance** để tạo instance thứ nhất
![Launch Instance](/images/ALBimg/launchinstance.png)

- Đặt tên cho **Instance**
- Chọn **Amazon Linux 2023 AMI (HVM)**
![Amazon Linux 2 AMI (HVM)](/images/ALBimg/createinstance-1.png)

- Chọn initance type là **t2.micro**
- click **tạo key peir mới**
![initance type](/images/ALBimg/instance-1-type.png)

- Đặt tên cho **key pair**        
- Chọn key pair là **RDS**       
- **Private key file formart** là **.pem**
- Click **Create key pair**      
![create key pair](/images/ALBimg/keypair-1.png?width=30pc)

- Phần security group chọn **Select existing security group**       
- Common security group chọn **default VPV**
![create key pair](/images/ALBimg/sgforinstance-1.png)

- Ở phần **Advanced details** chúng ta sẽ dùng script Bash để thiết lập nhanh một máy chủ web Apache trên một instance AWS EC2, đồng thời hiển thị địa chỉ IP (Private và Public) của instance trên trang web.
    - Copy đoạn script Bash phía dưới và dán vào **User data**
```bash
#!/bin/bash
yum install httpd -y
service httpd start
chconfig httpd on

cd /var/www/html
echo "<html>" > index.html

echo "<h1 style='color:blue;'>Welcome to Udemy instance - A</h1>" >> index.html
echo "<h4 style='color:red;'>You are running instance from this IP (For debug only!!!!Do not public this to user):</h4>" >> index.html

export TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`

echo "<br>Private IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/local-ipv4 >> index.html

echo "<br>Public IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-ipv4 >> index.html 
echo "</html>" >> index.html
```

![user data script](/images/ALBimg/user-data-1.png)

- Kiểm tra lại cấu hình và click **Launch instance**
- Cách tạo Instance thứ hai như giống như Instance thứ nhất nên bạn hãy tạo thêm một instance như cách trên.

---

>⚠️ **Lưu ý:** Đoạn script Bash của instance thứ hai sẽ khác của instance thứ nhất để chúng ta có thể phân biệt.

---

- Đoạn script Bash của instance thứ hai

```bash
#!/bin/bash
yum install httpd -y
service httpd start
chconfig httpd on

cd /var/www/html
echo "<html>" > index.html

echo "<h1 style='color:green;'>Welcome to Udemy instance - B</h1>" >> index.html
echo "<h4 style='color:red;'>You are running instance from this IP (For debug only!!!!Do not public this to user):</h4>" >> index.html

export TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`

echo "<br>Private IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/local-ipv4 >> index.html

echo "<br>Public IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-ipv4 >> index.html 
echo "</html>" >> index.html
```

- Đây là hai Instance sau khi được tạo thành công
![Done EC2 Server](/images/ALBimg/doneEC2.png)

- Kiểm tra inbound rules của security group và bổ xung phương thức HTTP nếu chưa có
- Chọn security group của một trong hai instance vừa tạo
![check security group](/images/ALBimg/checksg.png)
- Click vào **Edit Inbound rules**
![edit inbound rule](/images/ALBimg/editinboundrules.png)
- Click **Add rules** để thêm phương thức HTTP và click **Save rules**
![save inbound rule](/images/ALBimg/saverule.png)

- Để kiểm tra hai instance có hoạt động hay chưa, chúng ta sẽ mở tab mới và dán Public IP của từng insance 
![check IP](/images/ALBimg/checkinstance-01.png)
![check IP](/images/ALBimg/checkinstance-02.png)

- Mở tab mới và dán Public IP
![check web](/images/ALBimg/checkweb-01.png)
![check web](/images/ALBimg/checkweb-02.png)

- Tiếp theo chúng ta sẽ tạo Target group để thêm hai Instance vừa tạo
