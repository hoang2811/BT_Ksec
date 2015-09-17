##Tìm Hiểu Mô Hình OSI & TCP/IP

###I. Ưu điểm của việc dùng mô hình phân lớp:
* Giảm thiểu độ phức tạp của hệ thống dữ liệu.
* Chuẩn hóa giao diện các dòng sản phẩm.
=> Đảm bảo tính tương thích về mặt công nghệ.
* Thúc đẩy kỹ thuật modul hóa ( chuyên môn hóa).
* Đơn giản hơn trong việc dạy và học.

=> Giúp thúc đẩy sự phát triển của công nghệ mạng máy tính.

###II. Mô hình OSI (Open System Interconnection)

|7| Application|
|---|---------------|
|6| Presentation|
|5|Session|
|4|Transport|
|3|Network|
|2|Data Link|
|1|Physical|

####1. Lớp physical ( lớp vật lý)
- Truyền 1 đường bit qua 1 đường truyền vật lý cụ thể nào đó. ( xây dựng 1 đường truyền vật lý cho các host).
- Các đặc tính của lớp:
	+ Biểu diễn các bit.
	+ Mang đặc tính vật lý của giao diện và môi trường.
	+ Đồng bộ bit.
	+ Cấu hình đường dây.
	+ Tôpô mạng.
	+ Chế độ truyền.
	
####2. Data link ( Liên kết dữ liệu )
- Cung cấp, điều khiển việc truy nhập vào đường truyền vật lý và thực hiện chức năng giao tiếp với mạng bên trên.
- Các đặc tính:
	+ Tạo khung.
	+ Định (tạo) địa chỉ vật lý.
	+ Điều khiển lưu lượng.
	+ Kiểm tra lỗi.
	+ Điều khiển truy cập.
	
####3. Network layed ( lớp mạng)

* Phân phối dữ liệu (gói packet) từ điểm này đến điểm kia 1 cách tối ưu nhất.
* Các đặc tính:
	+ Định tuyến các gói packet.
	+ Chọn ra đường đi tối ưu nhất để phân phối dữ liệu.
	+ Định (tạo) địa chỉ logic (IP).
-	Các giao thức: IP, IPX, RIP…

####4. Transport layed (lớp vận chuyển)
- Quản lý kết nối đầu cuối, đầu cuối (End to End) hay có thể hiểu là chuyển toàn bộ bản tin từ thiết bị đầu cuối phát đến thiết bị đầu cuối thu.
- Chức năng, nhiệm vụ:
	+ Xử lý các vấn đề truyền dẫn, truyền tải giữa các host.
	+ Đảm bảo rằng dữ liệu được truyền tải 1 cách đáng tin cậy từ điểm này đến điểm kia trong mạng.
	+ Đảm bảo thiết lập, duy trì, kết thúc các đường mạch ảo.
	+ Cung cấp cơ chế sửa lỗi tin cậy, dò lỗi, phục hồi thông tin bằng cách điều khiển luồng.
-	Các giao thức : TCP, UDP, SPX

####5. Session (lớp phiên, kiểm soát)
- Lớp kiểm soát là lớp điều khiển đối thoại. Lớp này thiết lập, duy trì, giải phóng và đồng bộ hóa tương tác giữa các hệ thống thông tin.
- Sử dụng các giao thức: NFS (network file system), X- window system, ASP

####6. Presentation (lớp trình bày)

* Chức năng:
	+ Giúp dữ liệu từ đầu này được gửi đi có thể đọc được ở đầu kia nhận (biên dịch).
	+ Định dạng lại dữ liệu.
	+ Cấu trúc lại dữ liệu. 
	+ Thương lượng các cú pháp truyền dữ liệu cho lớp ững dụng (Lớp 7).
	+ Mã hóa.
	
####7. Application (lớp ứng dụng)
- Cung cấp các ứng dụng tương tác trực tiếp với người dùng (nhưu email, truyền file, các truy nhập từ xa,….)
- Ngoài ra, còn cung cấp cơ chế xác thực người dùng.
- Lớp đưa ra các giao thức: HTTP, FTP, SMTP, POP3, Telnet

###III. Cách thức hoạt động của mô hình OSI

![](http://imgur.com/FBSmUfw.png)

```
Kí hiệu: + L7H : Layer 7 header.
         + L2F : Trình sử lỗi FCS.
```
     
* Mô hình OSI là mô hình truyền tải dữ liệu đồng cấp. Đàu tiên khi máy tính cần gửi  dữ liệu (data) thì nó sẽ đi theo từ lớp 7 -> lớp 1, chuyển thành dãy bit nhị phân sau đó khi qua đến bên kia sẽ theo thứ tự ngược lại từ 1->7. Cụ thể là:
	* Khi các thông tin được đưa vào lớp 7 (Application) sẽ được chuyển xuống lớp 6 (Presentation) để mã hóa và nén dữ liệu.
	* Dữ liệu sẽ được chuyển xuống lớp 5 (Session) sẽ được bổ xung thêm thông tin về phiên giao dịch.
	* Tại lớp 4 (Transport) dữ liệu sẽ được cắt thành nhiều Segment và bổ xung thêm thông tin về phương thức vận chuyển.
	* Xuống lớp 3 (network) mỗi Segment sẽ được cắt ra thành nhiều Packet và bổ xung thêm thông tin định tuyến.
	* Ở lớp 2 (datalink) mỗi Packet lại cắt ra thành nhiều Frame bổ xung thêm thông tin kiểm tra gói tin. Ngoài ra ở lớp này còn có thêm quá trình kiểm tra lỗi FCS.
	* Đến lớp cuối cùng lớp 1 (physical) mỗi Frame sẽ được chuyển thành các bit 0 và 1 rồi được đẩy lên các phương tiện truyền dẫn. 
	* Sau khi qua đến bên máy nhận thì thực hiện quá trình ngược lại từ lớp 7 -> lớp 1.


###IV. Mô hình TCP/IP

![](http://i.imgur.com/ELlE7ni.png)

#####So sánh giữa mô hình OSI và TCP/IP

* Giống nhau:

	* Đều phân lớp chức năng
	* Đều có lớp vận chuyển và lớp mạng.
	* Chuyển gói là hiển nhiên.
	* Đều có mối quan hệ trên dưới, ngang hàng.
	
* Khác nhau:

	* TCP/IP gộp lớp trình bày và lớp phiên vào lớp ứng dụng.
	* TCP/IP gộp lớp vật lý và lớp liên kết dữ liệu vào lớp truy nhập mạng.
	* TCP/IP đơn giản vì có ít lớp hơn.
	* OSI không có khái niệm chuyển phát thiếu tin cậy ở lớp 4 như UDP của TCP/IP
