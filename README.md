Kiểm thử hiệu năng với Apache JMeter
1. Giới thiệu

Bài tập này nhằm mục đích giúp sinh viên làm quen với công cụ kiểm thử hiệu năng Apache JMeter và thực hiện các kịch bản kiểm thử tải cho các website.

Mục tiêu

Làm quen với công cụ kiểm thử hiệu năng JMeter

Thiết kế và thực thi các kịch bản kiểm thử với nhiều mức tải khác nhau

Phân tích kết quả kiểm thử dựa trên các chỉ số hiệu năng

Công cụ sử dụng

Apache JMeter

Java

JMeter GUI

GitHub

2. Website được kiểm thử

Các website được sử dụng trong bài kiểm thử:

Example Domain

VnExpress

Vietnamnet

3. Cấu trúc thư mục
<img width="197" height="233" alt="image" src="https://github.com/user-attachments/assets/7e387b7d-2856-418b-adc2-0d33c8aaca87" />

4. Mô tả Test Plan

Test Plan bao gồm 3 Thread Group, tương ứng với ba kịch bản kiểm thử hiệu năng khác nhau.

Mỗi Thread Group mô phỏng một số lượng người dùng khác nhau truy cập vào website nhằm đánh giá khả năng phản hồi của hệ thống.

5. Thread Group 1 – Kịch bản cơ bản
Mục tiêu

Kiểm tra phản hồi của website khi số lượng người dùng nhỏ.

Cấu hình
Number of Threads (Users): 10
Ramp-up Period: 10 seconds
Loop Count: 5
Method: HTTP GET
URL: https://example.com/

Website kiểm thử:

Example Domain

Kết quả mong đợi

Website phản hồi nhanh

Không xuất hiện lỗi

Error Rate = 0%
<img width="959" height="508" alt="image" src="https://github.com/user-attachments/assets/bf343b80-29c4-45c4-a19f-fa62a688daf9" />

Đánh giá

Website example.com là một trang web đơn giản nên thời gian phản hồi rất thấp và hệ thống hoạt động ổn định khi số lượng người dùng ít.

6. Thread Group 2 – Kịch bản tải trung bình
Mục tiêu

Đánh giá khả năng chịu tải của website khi số lượng người dùng tăng lên.

Cấu hình
Number of Threads (Users): 50
Ramp-up Period: 30 seconds
Loop Count: 1
Method: HTTP GET
URL: https://vnexpress.net/

Website kiểm thử:

VnExpress

Kết quả mong đợi

Thời gian phản hồi cao hơn so với Thread Group 1

Website vẫn hoạt động ổn định

Không xảy ra lỗi hệ thống

<img width="958" height="507" alt="image" src="https://github.com/user-attachments/assets/0fbfcb80-b36c-43e6-b298-c457f3d89b1c" />

Đánh giá

Do nội dung trang báo có nhiều hình ảnh và tài nguyên nên thời gian phản hồi cao hơn so với example.com. Tuy nhiên website vẫn hoạt động ổn định và không xảy ra lỗi trong quá trình kiểm thử.

7. Thread Group 3 – Kịch bản tùy chỉnh
Mục tiêu

Mô phỏng hành vi người dùng thực tế truy cập vào nhiều trang web khác nhau trong cùng một khoảng thời gian.

Cấu hình
Number of Threads (Users): 15
Ramp-up Period: 60 seconds
Duration: 60 seconds
Method: HTTP GET

Các website được kiểm thử:

VnExpress

Vietnamnet

HTTP Header Manager

Trong Thread Group 3 có cấu hình HTTP Header Manager với các header:

User-Agent
Accept
Accept-Language

Mục đích của việc thêm User-Agent là để mô phỏng trình duyệt thật và tránh việc website chặn request từ bot.
<img width="959" height="506" alt="image" src="https://github.com/user-attachments/assets/7599274b-44ac-4e3c-bf88-5d31278a87ef" />

8. Phân tích kết quả kiểm thử
8.1 Tổng quan

Kết quả kiểm thử được thu thập thông qua Summary Report của Apache JMeter.

Các chỉ số chính bao gồm:

Response Time

Throughput

Error Rate

8.2 Phân tích từng kịch bản
Thread Group 1 – Example.com

Response time thấp

Throughput cao

Không phát sinh lỗi

➡️ Website hoạt động rất ổn định khi số lượng người dùng thấp.

Thread Group 2 – VnExpress

Response time tăng do nội dung trang lớn

Throughput giảm nhẹ

Không phát sinh lỗi

➡️ Website vẫn hoạt động ổn định với số lượng người dùng cao hơn.

Thread Group 3 – VnExpress và Vietnamnet

Response time tương đối cao do nội dung trang báo có nhiều dữ liệu

Throughput ở mức trung bình

Không xuất hiện lỗi hệ thống

➡️ Các website tin tức vẫn hoạt động ổn định khi có nhiều request đồng thời.

8.3 Độ ổn định và lỗi

Trong quá trình kiểm thử:

Error Rate = 0%
Không xuất hiện lỗi HTTP 4xx hoặc 5xx
Không xảy ra timeout

Điều này cho thấy các website được kiểm thử hoạt động ổn định trong phạm vi tải đã cấu hình.

9. Kết luận

Qua bài tập này, sinh viên đã:

Làm quen với công cụ Apache JMeter

Biết cách tạo Test Plan, Thread Group và Listener

Hiểu cách thu thập và phân tích các chỉ số hiệu năng như:

Response Time
Throughput
Error Rate

Kiểm thử hiệu năng là một bước quan trọng giúp đảm bảo hệ thống web có thể hoạt động ổn định khi số lượng người dùng tăng cao.
