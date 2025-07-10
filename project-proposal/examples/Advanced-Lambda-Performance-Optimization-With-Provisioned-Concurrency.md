





Tên dự án : Advanced Lambda Performance Optimization với Provisioned Concurrency
Mô tả : Nghiên cứu và optimize Lambda performance với provisioned concurrency, memory tuning, runtime optimization, cold start elimination. Include cost analysis và monitoring. Yêu cầu: Performance benchmarking, cold start optimization (<100ms), memory profiling, cost optimization (>30% reduction), monitoring dashboard, auto-scaling policies, operational procedures.

Người thực hiện: Lê Như Tâm
Phòng ban: AWS























I. Tóm tắt nội dung
1. Tổng quan bối cảnh
Hiện nay, doanh nghiệp thương mại điện tử đang phải đối mặt với các vấn đề nghiêm trọng liên quan đến hạ tầng công nghệ thông tin khi lưu lượng người dùng tăng cao đột biến, đặc biệt trong các dịp khuyến mãi lớn hoặc sự kiện flash sale. Cụ thể, hệ thống cũ dựa trên máy chủ Amazon EC2 Auto Scaling Group yêu cầu duy trì tối thiểu từ ba đến năm máy chủ chạy thường trực để đảm bảo khả năng xử lý đơn hàng, dẫn đến chi phí hạ tầng hàng tháng rất cao và độ trễ khi khởi động máy chủ mới thường kéo dài từ năm đến mười phút.
Điều này không chỉ làm gia tăng chi phí vận hành, mà còn ảnh hưởng trực tiếp đến trải nghiệm khách hàng và khả năng duy trì doanh thu trong các giai đoạn cao điểm.
2. Mục tiêu và phạm vi giải pháp
Để giải quyết triệt để các vấn đề nêu trên, dự án đề xuất triển khai giải pháp Kiến trúc Serverless trên nền tảng dịch vụ AWS Lambda, kết hợp với cơ chế Provisioned Concurrency tự động mở rộng (Auto Scaling). Giải pháp này sẽ loại bỏ hoàn toàn nhu cầu duy trì máy chủ vật lý chạy liên tục, đồng thời đảm bảo ứng dụng có khả năng đáp ứng ngay lập tức khi tải tăng cao mà không gặp độ trễ khởi động.
Các đặc điểm nổi bật của giải pháp bao gồm:
-Tích hợp dịch vụ API Gateway để tiếp nhận và định tuyến các yêu cầu từ phía khách hàng đến hàm Lambda.
-Kích hoạt Lambda Provisioned Concurrency, đảm bảo số lượng phiên bản sẵn sàng xử lý yêu cầu ngay lập tức mà không bị ảnh hưởng bởi hiện tượng "cold start".
-Tự động mở rộng (scale out) số lượng concurrency từ một đến năm dựa trên các chỉ số hoạt động (metrics) thu thập từ dịch vụ Amazon CloudWatch.
-Giám sát liên tục và cảnh báo kịp thời khi tải tăng bất thường hoặc chi phí vượt mức dự kiến.
3. Lợi ích kinh doanh
Giải pháp đề xuất mang lại nhiều lợi ích cụ thể và rõ rệt cho doanh nghiệp, bao gồm:
-Tối ưu chi phí vận hành hạ tầng: Chi phí duy trì dự kiến giảm khoảng 35% so với mô hình máy chủ EC2 Auto Scaling trước đây, nhờ cơ chế chỉ tính phí khi Lambda thực sự hoạt động và không cần giữ máy chủ chạy thường trực.
-Nâng cao trải nghiệm khách hàng: Thời gian phản hồi dự kiến giảm từ ba đến năm giây (khi khởi động máy chủ mới) xuống dưới 500 mili giây, nhờ Provisioned Concurrency luôn giữ sẵn các phiên bản đã khởi động.
-Tăng độ tin cậy và khả năng mở rộng: Hệ thống tự động scale nhanh trong vài giây, đáp ứng khối lượng giao dịch lên tới mười nghìn yêu cầu mỗi phút mà không gián đoạn.
-Đơn giản hóa vận hành và bảo trì: Giảm đáng kể công việc quản trị máy chủ, nhờ kiến trúc serverless và giám sát tập trung qua CloudWatch.
Ngoài ra, thời gian triển khai ngắn gọn chỉ trong 4 tuần, giúp doanh nghiệp nhanh chóng đưa giải pháp vào vận hành thực tế. ROI dự kiến đạt sau 18 tháng, đảm bảo hiệu quả đầu tư và tính bền vững dài hạn.
4. Đầu tư, chi phí và thời gian triển khai
Chi phí triển khai dự kiến: Khoảng 180 đô la Mỹ mỗi tháng, bao gồm các khoản phí cho Lambda Provisioned Concurrency, API Gateway, CloudWatch Logs và các dịch vụ liên quan.
Thời gian triển khai dự kiến: 4 tuần, chia thành bốn giai đoạn chính:
-Khởi tạo môi trường và dịch vụ Lambda cơ bản.
-Cấu hình giám sát và cảnh báo qua CloudWatch.
-Kích hoạt chính sách tự động mở rộng Provisioned Concurrency.
-Kiểm thử hiệu năng, tối ưu tham số và đưa vào vận hành chính thức.
5. Các chỉ số đánh giá thành công và kết quả kỳ vọng
Giải pháp sẽ được coi là thành công nếu đáp ứng được các tiêu chí đo lường cụ thể sau:
-Giảm độ trễ phản hồi từ ba đến năm giây xuống dưới năm trăm mili giây trong điều kiện tải cao.
-Đảm bảo tỷ lệ xử lý đơn hàng thành công vượt 99,95%, không để thất thoát đơn hàng trong thời gian cao điểm.
-Giảm ít nhất 35% tổng chi phí hạ tầng hàng năm, so với mô hình Auto Scaling EC2 hiện tại.
-Rút ngắn thời gian triển khai tính năng mới, nhờ cơ chế tự động mở rộng mà không yêu cầu điều chỉnh hạ tầng thủ công.
6. Tầm nhìn dài hạn và giá trị chiến lược
Việc chuyển đổi từ hạ tầng dựa trên máy chủ truyền thống sang kiến trúc Serverless với Lambda Provisioned Concurrency không chỉ giải quyết nhu cầu hiện tại, mà còn tạo nền tảng vững chắc cho tương lai, giúp doanh nghiệp:
-Tối ưu vận hành và giảm rủi ro vận hành.
-Dễ dàng mở rộng sang các khu vực địa lý mới.
-Chủ động trong việc ứng phó với các chiến dịch marketing lớn.
-Gia tăng năng lực cạnh tranh trong ngành thương mại điện tử.
II. Tuyên bố vấn đề
1. Hiện trạng hệ thống
Hiện nay, hệ thống thương mại điện tử của doanh nghiệp đang sử dụng kiến trúc dựa trên nhóm máy chủ tự động mở rộng (Auto Scaling Group) với dịch vụ Amazon EC2. Mô hình này yêu cầu duy trì ít nhất ba đến năm máy chủ hoạt động liên tục, bất kể lưu lượng truy cập thực tế có thấp hay không.
Mỗi lần nhu cầu tăng đột biến, hệ thống cần khởi động thêm máy chủ mới, dẫn đến thời gian chờ khởi động trung bình từ năm đến mười phút. Trong khoảng thời gian đó, người dùng cuối sẽ gặp hiện tượng chậm trễ trong việc đặt hàng, thậm chí lỗi thời gian chờ (timeout).
Ngoài ra, tôi phải thường xuyên theo dõi và điều chỉnh quy mô thủ công, đặc biệt trong các chiến dịch khuyến mãi lớn hoặc sự kiện flash sale, để tránh tình trạng quá tải. Điều này vừa tốn nhân lực, vừa tiềm ẩn rủi ro gián đoạn dịch vụ.
2. Các thách thức chính
-Chi phí vận hành cao: Mỗi tháng, doanh nghiệp phải chi trả chi phí duy trì máy chủ dù không phải lúc nào cũng khai thác hết công suất.
-Thời gian phản hồi không ổn định: Khi khởi động máy chủ mới, độ trễ xử lý yêu cầu tăng đột biến.
-Khả năng mở rộng hạn chế: Trong thời điểm lưu lượng truy cập vượt dự đoán, Auto Scaling có độ trễ tự nhiên, không đáp ứng tức thì.
-Độ phức tạp quản lý: Đội ngũ vận hành cần trực tiếp giám sát, điều chỉnh thông số và xử lý sự cố, gây áp lực lớn về nhân lực.
3. Tác động đối với các bên liên quan
-Khách hàng cuối: Gặp trải nghiệm không nhất quán, dễ mất niềm tin và từ bỏ đơn hàng.
-Đội ngũ vận hành: Phải làm việc căng thẳng trong các giai đoạn cao điểm.
-Bộ phận kinh doanh: Doanh thu giảm sút nếu không xử lý kịp thời lưu lượng tăng.
-Ban giám đốc: Mất cơ hội gia tăng thị phần và hình ảnh thương hiệu.
4. Hậu quả nếu không khắc phục
Nếu tiếp tục duy trì kiến trúc cũ:
-Chi phí duy trì hạ tầng vẫn duy trì ở mức cao và không tối ưu hóa được.
-Hiệu suất hệ thống không thể cải thiện đáng kể, nhất là trong các dịp cao điểm.
-Khả năng mở rộng sẽ tiếp tục bị giới hạn bởi tốc độ khởi động máy chủ.
-Mức độ hài lòng khách hàng có nguy cơ suy giảm nghiêm trọng.
5. Cơ hội trên thị trường
Hiện nay, các doanh nghiệp thương mại điện tử đang chuyển đổi sang mô hình Serverless để:
-Giảm chi phí hạ tầng.
-Đảm bảo độ trễ thấp và khả năng phản hồi ngay lập tức.
-Tối ưu trải nghiệm khách hàng trong bối cảnh cạnh tranh ngày càng gay gắt.
Triển khai kiến trúc Lambda với Provisioned Concurrency chính là cơ hội để doanh nghiệp khẳng định vị thế tiên phong về công nghệ và nâng cao lợi thế cạnh tranh.
III. Kiến trúc Giải pháp
1. Mục đích
Thiết kế một kiến trúc kỹ thuật chi tiết giúp Lambda function đạt được:
-Tối ưu hóa cold start (thời gian khởi động lạnh)
-Tự động scale số lượng Provisioned Concurrency khi tải tăng
-Giám sát hiệu suất và chi phí tập trung
2. Tổng quan kiến trúc 
Hệ thống bao gồm các thành phần chính:
-API Gateway
Nhận request từ người dùng cuối hoặc hệ thống khác
Kích hoạt Lambda function
-Lambda Function (lambda-performance-test)
Xử lý logic nghiệp vụ
Được cấu hình Provisioned Concurrency để giảm latency
Tự động scale nhờ Auto Scaling Policy
-CloudWatch Logs & Metrics
Thu thập logs, metrics về số lần gọi, lỗi, thời gian thực thi
Tạo dashboard giám sát
-Application Auto Scaling
Điều chỉnh Provisioned Concurrency dựa trên policy mục tiêu
Đảm bảo số instance luôn phù hợp mức tải
3. Lý do lựa chọn AWS services

| Thành phần | Dịch vụ AWS | Lý do chọn |
| --- | --- | --- |
| Endpoint nhận request | API Gateway | Tích hợp dễ dàng Lambda, hỗ trợ scaling tự động |
| Xử lý nghiệp vụ | Lambda | Serverless, tính phí theo thời gian chạy, dễ quản lý |
| Scaling Provisioned Concurrency | Application Auto Scaling | Tự động scale số lượng concurrency instances |
| Giám sát & thông báo | CloudWatch | Tích hợp logs, metrics, alarm tập trung |

4. Tương tác giữa các thành phần 
-Người dùng gửi request tới API Gateway.
-API Gateway kích hoạt Lambda function lambda-performance-test.
-Lambda xử lý logic nghiệp vụ, trả về kết quả.
-Mỗi lần thực thi, CloudWatch ghi logs và metrics.
-Application Auto Scaling đọc metrics CloudWatch, quyết định scale Provisioned Concurrency lên hoặc xuống.
5. Kiến trúc bảo mật và tuân thủ 
-Lambda được giới hạn quyền theo IAM Role riêng:
Chỉ cho phép ghi logs vào CloudWatch.
Chỉ cho phép Application Auto Scaling quản lý Provisioned Concurrency.
-API Gateway được cấu hình:
Throttling để ngăn quá tải.
Resource Policy hạn chế IP hoặc VPC.
-Tất cả dữ liệu logs được lưu trong CloudWatch Logs để tuân thủ chuẩn bảo mật.
6. Khả năng mở rộng và hiệu năng
-Provisioned Concurrency đảm bảo Lambda luôn khởi động nhanh (cold start <100ms).
-Application Auto Scaling tự động tăng giảm số lượng instance dự phòng.
-API Gateway tự động scale theo số lượng request.
7. Tích hợp với hệ thống hiện có 
Nếu sau này mở rộng, Lambda có thể:
-Gọi DynamoDB, RDS hoặc S3
-Kết nối VPC private subnet
-Tích hợp SNS/SQS để xử lý async
8. Sơ đồ kiến trúc hệ thống
![Sơ đồ Kiến trúc 1](extracted_images/architecture_diagram_1.png)


IV. Triển khai Kỹ thuật
1. Mục đích
Trình bày chi tiết toàn bộ cách triển khai dự án, bao gồm:
Các giai đoạn thực hiện
-Yêu cầu kỹ thuật
-Phương pháp phát triển
-Chiến lược kiểm thử
-Kế hoạch triển khai
-Quản lý cấu hình
-Cách giảm thiểu rủi ro
2. Các giai đoạn thực hiện với các sản phẩm bàn giao

| Giai đoạn | Mô tả | Sản phẩm bàn giao (Deliverables) |
| --- | --- | --- |
| 1. Phân tích yêu cầu | Tìm hiểu chi tiết yêu cầu kỹ thuật và nghiệp vụ | Tài liệu yêu cầu chi tiết (Requirement Specification Document) |
| 2. Thiết kế kiến trúc | Thiết kế kiến trúc hệ thống, xác định các dịch vụ AWS và cách tích hợp | Sơ đồ kiến trúc (Architecture Diagram), tài liệu thiết kế |
| 3. Triển khai hạ tầng | Tạo Lambda function, API Gateway, CloudWatch, Application Auto Scaling | Tài nguyên AWS đã được triển khai trên tài khoản |
| 4. Cấu hình tự động Scaling | Đăng ký Provisioned Concurrency và gán Policy Auto Scaling | Cấu hình Auto Scaling hoàn chỉnh |
| 5. Kiểm thử | Thực hiện kiểm thử đơn vị, kiểm thử tích hợp và hiệu năng | Báo cáo kết quả kiểm thử |
| 6. Triển khai Production | Hoàn tất triển khai chính thức, giám sát hoạt động | Tài liệu hướng dẫn vận hành, kiểm tra hoạt động thực tế |

3. Yêu cầu kỹ thuật
Compute
-Lambda Function
Runtime: Python 3.9 hoặc Node.js 22.x
Memory: 128, 512, 1024 MB
Timeout: 10 giây
Provisioned Concurrency: từ 1 đến tối đa 5 instance
-Lưu trữ
-CloudWatch Logs để lưu toàn bộ logs thực thi
-Mạng
API Gateway Public Endpoint
Nếu cần bảo mật IP, sử dụng Resource Policy giới hạn CIDR
-Security
IAM Role riêng cho Lambda với quyền tối thiểu:
AWSLambdaBasicExecutionRole
ApplicationAutoScalingFullAccess (dành riêng cho scaling)
Quyền ghi logs CloudWatch
4. Phương pháp tiếp cận và phương pháp phát triển
-Mô hình phát triển: Agile Iterative (Triển khai từng phần, kiểm thử liên tục)
-Quy trình triển khai:
Phân tích và xác nhận yêu cầu
Triển khai thử nghiệm trên môi trường Dev
Kiểm thử và tinh chỉnh
Triển khai Production
-Công cụ hỗ trợ:
AWS CLI để triển khai hạ tầng
CloudFormation Template hoặc Terraform (nếu muốn tái sử dụng)
5. Chiến lược thử nghiệm

| Loại kiểm thử | Mục tiêu |
| --- | --- |
| Kiểm thử đơn vị | Đảm bảo Lambda xử lý đúng logic nghiệp vụ với dữ liệu giả lập |
| Kiểm thử tích hợp | Xác minh API Gateway kích hoạt Lambda và logs được ghi lại chính xác |
| Kiểm thử hiệu năng | Tạo tải cao (nhiều request/s) để kiểm tra Auto Scaling Provisioned Concurrency |
| Kiểm thử bảo mật | Đảm bảo IAM Role chỉ cấp quyền tối thiểu cần thiết |

6. Kế hoạch triển khai và thủ tục khôi phục
-Triển khai Production
Xác minh Lambda Function đã đăng ký Provisioned Concurrency.
Gán Alias prod.
Gắn Auto Scaling Policy.
Kích hoạt CloudWatch Alarm.
Gửi thử request để xác minh.
Cập nhật tài liệu hướng dẫn vận hành.
-Thủ tục khôi phục
Nếu xảy ra lỗi lớn:
Rollback Alias prod về Version trước.
Xóa cấu hình Auto Scaling tạm thời.
Khôi phục Lambda Version stable đã lưu.
Thông báo stakeholders.
7. Quản lý cấu hình
-Quản lý mã nguồn: GitHub
-Quản lý cấu hình hạ tầng: CloudFormation Template hoặc Terraform Script
-Quản lý version Lambda: Mỗi lần deploy tạo Version mới, gán Alias prod
-Lưu trữ logs: CloudWatch Logs nhóm riêng theo chức năng
V. Thời gian và Các Mốc Chính
1. Mục tiêu
Xây dựng kế hoạch chi tiết về tiến độ dự án, từ bước phân tích đến triển khai và bàn giao, giúp đảm bảo mọi hoạt động được kiểm soát chặt chẽ và có phương án dự phòng khi phát sinh rủi ro.
2. Phân tích giai đoạn dự án

| Giai đoạn | Thời gian dự kiến | Mô tả công việc chính |
| --- | --- | --- |
| 1. Thu thập và phân tích yêu cầu | 3 ngày | Làm việc với stakeholders để làm rõ yêu cầu nghiệp vụ và kỹ thuật, xác nhận phạm vi dự án. |
| 2. Thiết kế kiến trúc và giải pháp | 4 ngày | Thiết kế sơ đồ kiến trúc chi tiết, lựa chọn dịch vụ AWS, lập tài liệu kiến trúc. |
| 3. Triển khai hạ tầng thử nghiệm | 2 ngày | Tạo Lambda function, API Gateway, CloudWatch, Auto Scaling trong môi trường Dev/Test. |
| 4. Cấu hình Auto Scaling | 2 ngày | Đăng ký Provisioned Concurrency và gắn Policy Auto Scaling. |
| 5. Kiểm thử chức năng và hiệu năng | 3 ngày | Thực hiện kiểm thử đơn vị, tích hợp, hiệu năng với tải cao để xác minh hệ thống tự động scale. |
| 6. Chuẩn bị triển khai Production | 2 ngày | Hoàn thiện tài liệu, kiểm tra cuối cùng, dự phòng rollback, xác nhận sẵn sàng triển khai. |
| 7. Triển khai Production | 1 ngày | Chuyển môi trường Production, kiểm tra hoạt động thực tế, ghi nhận logs và thông báo hoàn thành triển khai. |
| 8. Giám sát và bàn giao | 3 ngày | Theo dõi vận hành, hướng dẫn sử dụng, bàn giao tài liệu và mã nguồn cho bên liên quan. |

3. Các mốc quan trọng với tiêu chí thành công

| Mốc quan trọng (Milestone) | Tiêu chí hoàn thành (Success Criteria) |
| --- | --- |
| Hoàn tất phân tích yêu cầu | Tài liệu yêu cầu được phê duyệt bởi stakeholders |
| Hoàn tất thiết kế kiến trúc | Sơ đồ kiến trúc và tài liệu giải pháp được duyệt |
| Triển khai thành công môi trường thử nghiệm | Tất cả các thành phần AWS hoạt động và được xác minh |
| Cấu hình Provisioned Concurrency và Auto Scaling hoàn chỉnh | Tự động scale hoạt động và alarms được kích hoạt khi cần thiết |
| Hoàn thành kiểm thử hiệu năng | Lambda function đạt yêu cầu thời gian phản hồi và tự động scale theo tải |
| Triển khai Production thành công | Endpoint Production hoạt động ổn định, logs ghi đầy đủ, không có lỗi nghiêm trọng |
| Bàn giao tài liệu và đào tạo | Stakeholders xác nhận đã nhận toàn bộ tài liệu và hướng dẫn sử dụng |


4. Nhận dạng phụ thuộc

| Hoạt động | Phụ thuộc |
| --- | --- |
| Thiết kế kiến trúc | Phải hoàn tất phân tích yêu cầu |
| Triển khai hạ tầng thử nghiệm | Thiết kế kiến trúc đã phê duyệt |
| Cấu hình Auto Scaling | Lambda function và Alias prod phải được tạo thành công |
| Kiểm thử hiệu năng | Cấu hình Auto Scaling đã hoàn chỉnh |
| Triển khai Production | Kiểm thử thành công, không có lỗi nghiêm trọng |
| Giám sát và bàn giao | Triển khai Production thành công |


5. Phân tích đường dẫn quan trọng
Đường dẫn quan trọng là chuỗi các công việc không thể trì hoãn vì sẽ ảnh hưởng trực tiếp tới tiến độ toàn dự án:
-Phân tích yêu cầu 
-Thiết kế kiến trúc 
-Triển khai hạ tầng thử nghiệm 
-Cấu hình Auto Scaling 
-Kiểm thử hiệu năng 
-Triển khai Production
Nếu bất kỳ công đoạn nào chậm trễ, dự án sẽ bị kéo dài tương ứng.
6.  Kế hoạch phân bổ nguồn lực
Nhân lực:
-Bạn tự thực hiện toàn bộ dự án, nên cần phân bổ thời gian hợp lý cho từng giai đoạn.
Công cụ hỗ trợ:
-AWS CLI / Console
-GitHub để lưu trữ mã nguồn và tài liệu
-CloudWatch để giám sát
-Postman / JMeter để kiểm thử tải
Lịch làm việc:
-Mỗi ngày 4-6 tiếng làm việc liên tục
-Dành thời gian backup và kiểm tra kỹ trước khi qua giai đoạn tiếp theo
7. Thời gian đệm cho rủi ro
Dành thêm 2 ngày dự phòng sau mỗi mốc quan trọng, đặc biệt cho:
-Sự cố triển khai dịch vụ AWS
-Lỗi kiểm thử hiệu năng
-Thời gian phê duyệt thiết kế hoặc tài liệu
VI. Ước tính Chi phí
1. Mục tiêu
Cung cấp ước tính chi tiết và chính xác về chi phí xây dựng, vận hành và duy trì dự án trên môi trường AWS, đồng thời phân tích lợi tức đầu tư (ROI) và chiến lược tối ưu hóa chi phí để đảm bảo hiệu quả tài chính lâu dài.
2. Chi phí cơ sở hạ tầng AWS	
Dựa trên AWS Pricing Calculator, ngân sách hàng tháng dự kiến như sau:

| Thành phần | Dịch vụ AWS | Chi phí hàng tháng (ước tính) |
| --- | --- | --- |
| Máy chủ chức năng (Serverless) | AWS Lambda | $15 (tính trên ~5 triệu request/tháng và 1GB memory/provisioned concurrency) |
| API Management | Amazon API Gateway | $20 |
| Lưu trữ logs | Amazon CloudWatch Logs | $10 |
| Provisioned Concurrency | Lambda Provisioned Concurrency | $25 (5 concurrency) |
| Giám sát và cảnh báo | CloudWatch Alarms | $5 |
| Auto Scaling | Application Auto Scaling | Miễn phí (included) |


Tổng chi phí cơ sở hạ tầng hàng tháng (ước tính): $75 / tháng
Tổng chi phí cơ sở hạ tầng hàng năm: $900 / năm
3. Chi phí phát triển

| Danh mục | Chi phí ước tính |
| --- | --- |
| Phân tích yêu cầu, thiết kế kiến trúc | Không tốn chi phí thuê ngoài vì tự thực hiện |
| Triển khai hạ tầng | Không tốn chi phí thuê ngoài |
| Kiểm thử hiệu năng và tối ưu | Không tốn chi phí thuê ngoài |
| Tài liệu và đào tạo | Không tốn chi phí thuê ngoài |

4. Dịch vụ và giấy phép của bên thứ ba

| Dịch vụ / Công cụ | Chi phí |
| --- | --- |
| Github (Public repo) | Miễn phí |
| Draw.io / Lucidchart (miễn phí) | Miễn phí |
| Postman | Miễn phí (phiên bản cá nhân) |

5. Chi phí vận hành
Chi phí hàng tháng: $75
Chi phí vận hành khác: Không phát sinh thêm do không có nhân viên quản trị riêng.
Tổng chi phí vận hành hàng năm: $900
6. Tính toán ROI và phân tích điểm hòa vốn
Giả sử mục tiêu:
-Triển khai hệ thống hỗ trợ xử lý gấp đôi lượng request so với kiến trúc cũ (ước tính giảm thời gian downtime ~20%)
-Tăng hiệu suất xử lý giúp tiết kiệm chi phí nhân sự ~ $2,000/năm

| Hạng mục | Giá trị ước tính |
| --- | --- |
| Chi phí đầu tư ban đầu (năm đầu) | $900 |
| Chi phí vận hành năm tiếp theo | $900/năm |
| Lợi ích tài chính (tiết kiệm) | $2,000/năm |
| ROI năm đầu tiên | ($2,000 - $900) / $900 = 122% |
| Thời gian hoàn vốn | ~5-6 tháng |


Kết luận:
Giải pháp dự kiến đạt ROI hơn 120% ngay trong năm đầu và có chi phí vận hành duy trì hợp lý về lâu dài.
7. Chiến lược tối ưu hóa chi phí
-Sử dụng Free Tier và Credits (nếu có):
AWS Free Tier cho Lambda và CloudWatch có thể giảm chi phí 10-20% ban đầu.
-Thiết lập cảnh báo chi phí:
Dùng AWS Budgets để đặt giới hạn và cảnh báo.
-Provisioned Concurrency tối ưu:
Chỉ bật Provisioned Concurrency trong khung giờ cao điểm.
-Tối ưu CloudWatch Logs retention:
Giới hạn lưu logs tối đa 30 ngày.
-Kiểm tra chi phí định kỳ:
Mỗi tháng xem Cost Explorer để điều chỉnh cấu hình nếu phát sinh chi phí bất thường.
 VII. Đánh giá Rủi ro
1. Mục đích
Phân tích toàn diện các rủi ro có thể ảnh hưởng đến tiến độ, chi phí và hiệu quả của dự án. Qua đó, đề xuất các chiến lược giảm thiểu rủi ro, kế hoạch dự phòng và phương án giám sát nhằm đảm bảo dự án được triển khai suôn sẻ và đạt mục tiêu đề ra.
2. Xác định rủi ro

| Mã rủi ro | Loại rủi ro | Mô tả chi tiết |
| --- | --- | --- |
| R01 | Kỹ thuật | Cấu hình Lambda Provisioned Concurrency không đúng dẫn đến độ trễ cao |
| R02 | Hoạt động | Chi phí AWS tăng đột ngột do lưu lượng lớn hoặc cấu hình sai |
| R03 | Con người | Thiếu kỹ năng vận hành AWS gây chậm tiến độ hoặc lỗi triển khai |
| R04 | Kinh doanh | Giải pháp không mang lại hiệu quả ROI như kỳ vọng nếu không có đủ người dùng |
| R05 | Bảo mật & tuân thủ | Dữ liệu log nhạy cảm bị lưu giữ quá thời gian cần thiết hoặc chưa được mã hóa đúng |

3. Ma trận rủi ro

| Mã rủi ro | Tác động | Khả năng xảy ra | Mức độ ưu tiên |
| --- | --- | --- | --- |
| R01 | Cao | Trung bình | Cao |
| R02 | Trung bình | Cao | Cao |
| R03 | Trung bình | Trung bình | Trung bình |
| R04 | Trung bình | Thấp | Thấp |
| R05 | Cao | Thấp | Trung bình |

4. Chiến lược giảm thiểu

| Mã rủi ro | Chiến lược giảm thiểu |
| --- | --- |
| R01 | Thiết lập môi trường thử nghiệm riêng để test concurrency, tích hợp Auto Scaling để tránh manual config |
| R02 | Đặt CloudWatch Alarm cảnh báo chi phí; giới hạn concurrency theo thời gian; dùng AWS Budget |
| R03 | Tham khảo tài liệu AWS chính thức; sử dụng AWS Well-Architected Tool; học online bổ sung |
| R04 | Nghiên cứu thị trường kỹ hơn; triển khai MVP sớm để lấy feedback sớm |
| R05 | Thiết lập retention policy cho log; sử dụng mã hóa CloudWatch logs; chỉ lưu log cần thiết |

5. Kế hoạch dự phòng

| Mã rủi ro | Phương án dự phòng |
| --- | --- |
| R01 | Quay lại chạy Lambda không provisioned; dùng Lambda reserved concurrency tạm thời |
| R02 | Tạm thời scale down thủ công hoặc disable non-critical functions nếu vượt ngân sách |
| R03 | Tìm mentor hỗ trợ tạm thời; trì hoãn release giai đoạn để kịp training bổ sung |
| R04 | Tập trung vào một module có khả năng mở rộng hoặc pivot giải pháp |
| R05 | Xoá log cũ thủ công hoặc chuyển sang lưu trữ thấp hơn như S3 Glacier |

6. Quy trình giám sát
-Thiết lập hệ thống CloudWatch Dashboards để theo dõi:
Chi phí
Invocation count
Provisioned concurrency usage
-Cài đặt CloudWatch Alarms cho các rủi ro chính:
Cảnh báo nếu concurrency vượt mức cho phép
Cảnh báo nếu chi phí Lambda > $X/tháng
Cảnh báo khi lỗi xảy ra > X lần/ngày
-Thiết lập chu kỳ đánh giá hàng tuần:
Rà soát hiệu năng và logs
Rà soát billing trên AWS Cost Explorer
Ghi nhận các thay đổi lớn vào log nhật ký vận hành
-Nếu rủi ro vượt tầm kiểm soát:
Escalate lên quản lý cấp trên (nếu có team)
Tạm dừng chức năng rủi ro cao và phân tích lại
VIII. Kết quả kỳ vọng
1.Mục đích
Xác định rõ ràng các kết quả kỹ thuật và kinh doanh mà dự án hướng đến, bao gồm các chỉ số đo lường thành công, lợi ích theo từng giai đoạn và giá trị chiến lược dài hạn.
2. Các chỉ số thành công

| Loại | Chỉ số cụ thể |
| --- | --- |
| Kỹ thuật | - Giảm thời gian phản hồi Lambda xuống dưới 300ms trong 95% request- Tự động mở rộng Provisioned Concurrency theo tải sử dụng Application Auto Scaling |
| Hiệu suất | - Đạt khả năng xử lý tối thiểu 50.000 requests/ngày mà không gián đoạn dịch vụ |
| Kinh doanh | - Giảm chi phí vận hành >=30% so với phương pháp thủ công- Đạt uptime > 99.95% |
| Trải nghiệm UX | - Tăng tốc độ phản hồi API => cải thiện trải nghiệm người dùng đầu cuối rõ rệt |


3. Lợi ích ngắn hạn (0 – 6 tháng)
-Triển khai thành công kiến trúc tự động scale Lambda
-Đảm bảo hiệu năng ổn định ngay cả khi tải tăng đột biến
-Xây dựng quy trình DevOps cơ bản với CloudWatch Monitoring và Alarm
-Nắm bắt rõ hơn cách làm việc với các dịch vụ AWS nâng cao như Application Auto Scaling, Lambda Alias, CloudWatch Metrics
4. Lợi ích trung hạn (6 – 18 tháng)
-Tối ưu chi phí thông qua tự động scale đúng nhu cầu
-Mở rộng hệ thống để phục vụ nhiều dịch vụ hơn
-Giảm thời gian downtime khi deploy bằng cách sử dụng alias versioning
-Tăng độ tin cậy cho các ứng dụng real-time hoặc high-frequency
5. Giá trị dài hạn (18+ tháng)
-Hạ tầng serverless có thể tái sử dụng cho nhiều microservice khác
-Tích hợp thêm các giải pháp machine learning hoặc AI trên nền tảng đã ổn định
-Chuẩn hóa mô hình triển khai AWS theo hướng Enterprise-ready
-Đạt độ tin cậy cao (resilient) và khả năng mở rộng gần như vô hạn
6. Cải thiện trải nghiệm người dùng 
-Giảm độ trễ phản hồi ngay cả vào giờ cao điểm
-Người dùng không gặp lỗi timeout hoặc “cold start” do Lambda đã sẵn sàng từ trước (Provisioned Concurrency)
-Tăng độ tin cậy và độ chuyên nghiệp của ứng dụng từ góc nhìn người dùng
7. Khả năng chiến lược đạt được 
-Sở hữu khả năng tự động scale và kiểm soát chi phí phù hợp với chiến lược tăng trưởng dài hạn
-Khả năng mở rộng hệ thống mà không cần viết lại logic hạ tầng
-Tăng khả năng sẵn sàng phục vụ các mô hình kinh doanh có lượng truy cập lớn
-Tích hợp vào CI/CD pipeline với zero downtime deployment qua Lambda aliases
IX. Phụ lục
1. Thông số kỹ thuật

| Thành phần | Mô tả chi tiết |
| --- | --- |
| Ngôn ngữ lập trình | Python 3.12 cho Lambda Functions |
| Framework/API Gateway | RESTful API sử dụng Amazon API Gateway |
| Compute | AWS Lambda với Provisioned Concurrency |
| Provisioned Concurrency | Tối thiểu 1 - tối đa 5 (auto scaling) |
| Dữ liệu giám sát | Amazon CloudWatch Logs, Metrics, Alarms |
| Region triển khai | ap-southeast-1 (Singapore) |
| Mô hình triển khai | Alias-based deployment (prod, test alias) |
| Security | IAM Role với permission RegisterScalableTarget, PutScalingPolicy,... |
| Monitoring | CloudWatch Alarm for latency và invocation threshold |
| Tự động scale | AWS Application Auto Scaling cho Lambda |


2. Tính toán chi phí
Chi phí ước tính theo AWS Pricing Calculator – 
Chi phí cơ sở hạ tầng

| Dịch vụ | Ước tính sử dụng | Chi phí ước tính (USD/tháng) |
| --- | --- | --- |
| AWS Lambda (Provisioned) | 2M requests/tháng + 128MB RAM + 5 PCU | ~$6.40 |
| API Gateway | 1 triệu request đầu + 1 GB data | ~$3.50 |
| CloudWatch Logs | 5 GB logs + 5 alarms | ~$2.00 |
| Auto Scaling Policies | Không tính thêm | $0.00 |
| Tổng cộng hàng tháng |  | ~$11.90/tháng |

Chi phí phát triển một lần

| Khoản mục | Chi phí ước tính (USD) |
| --- | --- |
| Phát triển Lambda & API | $100 |
| Cấu hình Auto Scaling + Alarm | $50 |
| Kiểm thử và tinh chỉnh | $50 |
| Tổng cộng một lần | $200 |


3. Tính toán hoàn vốn
-Hiện tại: xử lý 2 triệu requests thủ công => chi phí vận hành cao hơn (~$20/tháng)
-Sau khi áp dụng: chi phí giảm còn ~$11.90/tháng
-ROI: tiết kiệm ~40% chi phí hàng tháng
-Điểm hòa vốn: sau 3 tháng sử dụng
4. Sơ đồ kiến ​​trúc

Tổng quan về thành phần
![Sơ đồ Kiến trúc 2](extracted_images/architecture_diagram_2.png)
-API Gateway nhận HTTP requests từ client.
-Lambda Function xử lý logic (vd: xử lý biểu mẫu, tính toán, phản hồi).
-Alias prod trỏ đến phiên bản ổn định nhất của function (v2).
-Provisioned Concurrency giữ cho Lambda luôn “warm”.
-Application Auto Scaling điều chỉnh concurrency theo tải.
-CloudWatch Alarms theo dõi số lượng invocation và độ trễ để tự động điều chỉnh.
5. Tài liệu tham khảo

-AWS Official Docs:



-AWS Pricing Calculator: 
-AWS Architecture Icons: 
-AWS FCJ Internship Project Proposal Guide: 





![Hình 1](extracted_images/image_1.png)

![Hình 2](extracted_images/image_2.png)
