+++
title = "Giới thiệu Application Load Balancing - AWS"
date = "2024-12-11"
weight = 1
chapter = false
+++

# Giới thiệu Application Load Balancing – AWS

#### Tổng quan
Application Load Balancer (ALB) là một dịch vụ cung cấp khả năng phân phối lưu lượng ứng dụng đến nhiều máy chủ backend nhằm đảm bảo hiệu suất và độ sẵn sàng cao của ứng dụng. ALB là một thành phần trong dịch vụ Elastic Load Balancing (ELB) của Amazon Web Services (AWS).

#### Ứng dụng       
- Phù hợp với các ứng dụng web hoặc API yêu cầu khả năng định tuyến phức tạp.     
- Tối ưu cho các kiến trúc microservices nhờ vào khả năng định tuyến linh hoạt.       
- Được sử dụng trong môi trường DevOps để quản lý lưu lượng đến các phiên bản dịch vụ khác nhau.      
  
#### Lợi ích của việc sử dụng Elastic Load Balancing
- Cải thiện hiệu suất ứng dụng.
- Tăng khả năng chịu lỗi nhờ tính năng cân bằng tải và tự động chuyển hướng lưu lượng.
- Đơn giản hóa việc quản lý giao thức HTTPS và bảo mật.     

#### Mô hình thực hành bài Lab
![Mô hình](/images/ALBimg/digram.png?width=800)

#### Nội dung chính
1. [Tạo EC2](1-Create-EC2/)
2. [Tạo Target Group](2-Create-Target-Group/)
3. [Tạo Load Balancer](3-Create-Load-Balancer/)
4. [Dọn dẹp tài nguyên](4-Clean-up-resources/)
