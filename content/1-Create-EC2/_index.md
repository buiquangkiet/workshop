+++
title = "Create EC2"
date = 2021
weight = 1
chapters = false
pre = "<b>1. </b>"
+++

> **Note:** We will use default VPC and Subnet to quickly create EC2

- Access **AWS Management Console:**
 - Navigate to EC2
 - Click Instances

![AWS Management Console](https://000003.awsstudygroup.com/images/4-CreateEc2Server-update/1-Create-EC2-Server/EC2-img1.png?featherlight=false&width=60pc)

- Click on **Launch Instance** to create the first instance
![Launch Instance](/images/ALBimg/launchinstance.png)

- Name **Instance**
- Select **Amazon Linux 2023 AMI (HVM)**
![Amazon Linux 2 AMI (HVM)](/images/ALBimg/createinstance-1.png)

- Select initance type as **t2.micro**
- click **create new key peir**
! [initance type](/images/ALBimg/instance-1-type.png)

- Name the **key pair**
- Select the key pair as **RDS**
- **Private key file format** as ** .pem**
- Click **Create key pair**
![create key pair](/images/ALBimg/keypair-1.png?width=30pc)

- In the security group section, select **Select existing security group**
- Common security group select **default VPV**
![create key pair](/images/ALBimg/sgforinstance-1.png)

- In the **Advanced details** section we will use a Bash script to set Quickly set up an Apache web server on an AWS EC2 instance, and display the instance's IP address (Private and Public) on the web page. - Copy the Bash script below and paste it into **User data**
```bash
#!/bin/bash
yum install httpd -y
service httpd start
chconfig httpd on

cd /var/www/html
echo "<html>" > index.html

echo "<h1 style='color:blue;'>Welcome to Udemy instance - A</h1>" >> index.html
echo "<h4 style='color:red;'>You are running instance from this IP (For debug only!!!!Do not publish this to user):</h4>" >> index.html

export TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`

echo "<br>Private IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/local-ipv4 >> index.html

echo "<br>Public IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-ipv4 >> index.html
echo "</html>" >> index.html
```

![user data script](/images/ALBimg/user-data-1.png)

- Check the configuration again and click **Launch instance**
- How to create second Instance as same as first Instance so you create another instance as above.

---

>⚠️ **Note:** The Bash script of the second instance will be different from the first instance so we can distinguish.

---

- Bash script of the second instance

```bash
#!/bin/bash
yum install httpd -y
service httpd start
chconfig httpd on

cd /var/www/html
echo "<html>" > index.html

echo "<h1 style='color:green;'>Welcome to Udemy instance - B</h1>" >> index.html
echo "<h4 style='color:red;'>You are running instance from this IP (For debug only!!!!Do not publish this to user):</h4>" >> index.html

export TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"`

echo "<br>Private IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/local-ipv4 >> index.html

echo "<br>Public IP: " >> index.html
curl -H "X-aws-ec2-metadata-token: $TOKEN" -v http://169.254.169.254/latest/meta-data/public-ipv4 >> index.html
echo "</html>" >> index.html
```

- These are the two Instances after being successfully created
![Done EC2 Server](/images/ALBimg/doneEC2.png)

- Check the inbound rules of the security group and add HTTP method if not present
- Select security group of one of the two instances just created
![check security group](/images/ALBimg/checksg.png)
- Click **Edit Inbound rules**
![edit inbound rule](/images/ALBimg/editinboundrules.png)
- Click **Add rules** to add a method HTTP and click **Save rules**
![save inbound rule](/images/ALBimg/saverule.png)

- To check if the two instances are working, we will open a new tab and paste the Public IP of each instance ![check IP](/images/ALBimg/checkinstance-01.png)
![check IP](/images/ALBimg/checkinstance-02.png)

- Open a new tab and paste the Public IP
![check web](/images /ALBimg/checkweb-01.png)
![check web](/images/ALBimg/checkweb-02.png)

- Next we will create Target group to add the two newly created Instances