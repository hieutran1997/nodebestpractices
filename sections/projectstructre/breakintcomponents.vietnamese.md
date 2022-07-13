# Tổ chức dự án dưới dạng component

<br/><br/>

### Đặt vấn đề

Đối với các ứng dụng vừa trở lên, monoliths thật không tốt để áp dụng, việc 1 phần mềm lớn có rất nhiều phụ thuộc và khó kiểm soát phụ thuộc có thể dẫn đến code cực rối. Ngay cả những kiến trúc sư phần mềm có nhiều kinh nghiệm trong việc module hoá ứng dụng lớn cũng danh nhiều nỗ lực để thiết kế, với mỗi thay đổi về ràng buộc cũng phải đánh giá rất cẩn thận các tác động đến các đối tượng phụ thuộc khác. Cách tốt để thực hiện là phát triển dự án lớn từ các dự án nhỏ, sao cho các dự án nhỏ này cô lập với nhau về chức năng cũng như không chia sẻ file cho nhau, ví dụ với 1 chức năng được cấu thành từ nhiều file khác nhau như: Controller, service, data access, test, ... từ đó có thể dễ dàng hiểu được logic hoạt động để sửa chữa nâng cấp. Một vài người gọi đây là kiến trúc microservices - điều quan trọng ở đây phải hiểu microservices không phải là 1 thông số mà bạn phải tuân theo, mà nó là tập hợp các nguyên tắc. Tuy nhiên bạn có thể áp dụng toàn bộ nguyên tắc vào 1 ứng dụng microservice hoặc 1 vài. Cả hai đều tốt miễn là bạn luôn giữ được sự đơn giản của phần mềm. Đơn giản bạn nên tạo sự cô lập giữa các components, phân bổ các thư mục của từng thành phần nghiệp vụ và tạo cho chúng độc lập với nhau, cho phép các compnents được trao đổi với nhau thông qua các lớp interface hoặc API. Đây là yếu tố cốt lõi để giữ cho các component của bạn đơn giản, tránh phụ thuộc chéo không rõ ràng => Đây là cách toàn diện của microservice trong tương lai khi mà ứng dụng của bạn lớn lên. 

<br/><br/>

### Trích dẫn: "Scaling requires scaling of the entire application" (Tạm dịch: Việc mở rộng ứng dụng thì cần phải mở rộng toàn bộ ứng dụng)

 Từ blog [MartinFowler.com](https://martinfowler.com/articles/microservices.html)

> Những ứng dụng Monolithic có thể thành công, nhưng ngày càng có nhiều người không còn hứng thú với nó, nhất là với các ứng dụng triển khai trên cloud. Các quy trình thay đổi gắn liền với nhau - với 1 thay đổi nhỏ trong 1 phần nghiệp vụ nhỏ của ứng dụng, yêu cầu ứng dụng monolithic phải rebuilt và deploy lại. Theo thời gian, thật khó để giữ một cấu trúc module tốt, dẫn đến việc ảnh hưởng từ những thay đổi nhỏ đó sẽ làm ảnh hưởng đến toàn bộ ứng dụng. Việc mở rộng toàn bộ ứng dụng sẽ khó hơn việc thay đổi 1 phần của nó.

<br/><br/>

### Trích dẫn: "So what does the architecture of your application scream?" (Tạm dịch: Kiến trúc ứng dụng của bạn nói lên điều gì?)

 Từ blog [uncle-bob](https://8thlight.com/blog/uncle-bob/2011/09/30/Screaming-Architecture.html) 

> ...Nếu bạn nhìn kiến trúc của 1 thư việc sách, bạn sẽ thấy lối vào rộng lớn, khu vực quầy check-in, check-out, khu vực đọc, phòng hội thảo nhỏ, các kệ sách liên tiếp nhau giữ sách cho cả thư viện. Kiến trúc đó nói lên nó là Thư viện.   

Kiến trúc của bạn nói lên điều gì? Khi bạn nhìn thấy folder ngoài cùng của kiến trúc, và sources file trên gói cấp cao nhất bạn sẽ đánh giá đây là Health Care System, hoặc Accounting System, hoặc Inventory Management System? Hoặc Rails, hoặc Spring/Hibernate, hoặc ASP? 

<br/><br/>

### Tốt: Cấu trúc độ lập giải pháp của bạn theo từng thành phần

![alt text](../../assets/images/structurebycomponents.PNG "Structuring solution by components")

<br/><br/>

### Không tốt: Nhóm các files theo vai trò kỹ thuật của chúng

![alt text](../../assets/images/structurebyroles.PNG "Structuring solution by technical roles")
