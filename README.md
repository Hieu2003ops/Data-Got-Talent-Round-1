# Datagottalen team 42
## Tien xu ly: 
  ### Môi trường làm việc: Python
  ### File dữ liệu xử lý : Xử lý qua jupyter/annaconda và file excel
  ### Quy trình tiền xử lý dữ liệu: 
    Tiền xử lý bằng python trên file jupyter:
      -- Sử dụng ngôn ngữ python và làm việc trên fie jupyter trên annaconda để thực hiện tiền xử lý dữ liệu từ bộ dữ liệu gốc mà ban tổ chức cung cấp. Bắt đầu xử lý với bảng customer , sau đó đến bảng tickets và cuối cùng làm việc với bảng films. Các bước thực hiện tiền xử lý ở mỗi bảng là : 
      -- Với bảng Customer: 
        Thực hiện lại việc chuẩn hóa lại cột DOB thành ngày tháng năm sau đó tạo một cột mới là tuổi xem phim bằng cách lấy tháng 5 năm 2019 từ cho giá trị của cột DOB sau khi đã tiền xử lý 
        Gán những missing value của cột industry thành Nojob
        Gán những missing value của cột Website thành không có dữ liệu
        Tạo 1 cột mới tên là Dữ liệu Web mang 2 giá trị là "No Data Website" và "Have Data Website" dựa vào giá trị của cột Website
        Xử lý cột address thành 3 cột đường , quận và thành phố 
        Xử lý các cột dữ liệu DOB bị lỗi sau khi chuẩn hóa 
      -- Với bảng Tickets:
        Thực hiện kiểm tra giá trị trùng lặp của orderid. Nhận ra có quá nhiều orderid bị trùng =>> không thể lọc được như bình thường. Nhóm nhận ra có tận 33039 dòng bị trùng => có nhiều khách hàng mua nhiều lần. Tiếp theo thực hiện kiểm tra xem có missing value ở cột orderid thì kết quả nhóm kiểm tra được là có 96 dòng có missing value. Nhóm đặt lại các orderid cho các missing value của cột orderid
        Nhóm thực hiện kiểm tra với cột cashier và nhận thấy không có missing value tại cột cashier, đồng thời với cột cashier thì thực hiện kiểm tra và nhận thấy tại cột cashier có các giá trị là từ emp001 đến emp010 và có giá trị website (đặt online qua web)
        Nhóm tiếp tực thực hiện kiểm tra cột customerid và nhận thấy có khoảng 3 khách đặt rất nhiều do với những khách còn lại. Có một vị khách chiếm đến 1/3 so với tổng doanh thu rạp có được 
        Nhóm tiếp tục làm việc với cột popcorn và nhận thấy có missing value , sau đó nhóm đã thay thế missing value bằng giá trị "Website/Liên Hệ tại quầy"
        Thực hiện tách cột saledate ra thành 2 cột saletime và saledate. Những giá trị null của cột saledate đã được thay thế bằng nhưng giá trị tương ứng với cột Date
        Tiếp tục nhóm thực hiện phân tích với cột Ticket type thì nhận ra sẽ có 2 loại vé chính là vé Đơn và vé Đôi
        Thực hiện việc xử lý cột ticket price thì nhms nhận ra là không có trường hợp bị missing value tại ticket price. Có 4 mức giá ở ticketprice và có 1 trường hợp bị nhầm lẫn tại ticketprice. 4 mức giá là 45000 cho vé đơn và 90000 cho vé đôi (áp dụng với mọi ngày trừ ngày lễ 0. Vào ngày lễ , với bộ dữ liệu mà ban tổ chức cung cấp cho nhóm thì giá vé sẽ tăng từ 45000 lên 75000 cho vé đơn và 160000 cho vé đôi. Đồng thời các vé đôi cũng chỉ áp dụng cho 2 phòng của rạp là phòng chiếu 1 và phòng chiếu 2
        Các phim được chiếu vào ngày quốc lễ (1/5/2019) thì sẽ chủ yếu ở 2 film là "MẸ MA THAN KHÓC" và "Avenger"
        Đối với giá vé bị nhập lỗi (ticket price) bằng 0 thi nhóm đã kiểm tra và nhận thấy rằng giá vé vào ngày này là giá vé đơn và không phải chiếu vào ngày quốc lễ nên nhóm đã thay thế giá trị 0 bằng 45000 đúng với format của dataset ban tổ chức cung cấp
        Tiếp theo với 2 cột total và saletime(được tách ra từ saledate) thì nhóm cũng xử lý các missing value đúng với yêu cầu , riêng với saletime ở missing value nhóm thay thế bằng giá trị "Không xác định rõ "
    Tiền xử lý bằng excel :
      -- Với bảng Films: 
        Dựa theo những cột có sẵn trong bảng Films ban đầu, thực hiện thêm những Films còn thiếu có trong bảng Tickets. Dữ liệu của phim được lấy từ trang "imdb.com" và "cgv.vn" 
        Cột cấp độ nhãn dán phim chiếu rạp "rating" được chuyển về một dạng thống nhất theo luật cấp độ nhãn dán Việt Nam cũ (2019) thành cột "vietnam rating" với: P (phim cho mọi lứa tuổi), C13 (phim cho người 13 tuổi trở lên), C16 (phim cho người 16 tuổi trở lên), C18 (phim cho người 18 tuổi trở lên).
        Nhóm đã thêm cột "imdb rating" để từ đó phân tích kết quả phim thực tế so với đánh giá phim của imdb.  
      -- Với 2 bảng customer và tickets đã xử lý trước bằng python
        Thực hiện xử lý cột tuổi trong bảng customer , dùng hàm if và hàm Vlook-up để đối chiếu rating và từ đó so sánh cột tuổi gốc để cho ra tuổi cuối cùng. 
        Check lại giá trị cột Quận , thay thế các giá trị "Không xác định rõ" đúng với thực tế của quận 
        Thêm cột ticket price bằng việc sử dụng python , sau đó bổ sung vào file excel , sheet customer
        Bảng ticket được merge với bảng film
        Tách các thể loại thành các cột và cho ra số tiền vé của từng cột để dễ dàng tính tổng doanh thu theo thể loại
  ## Trực quan hóa và làm báo cáo :
  ### Môi trường làm việc : Tableau
    Sử dụng môi trường Tableau để trực quan hóa bộ dữ liệu đã qua xử lí. Bắt đầu việc với trực quan hóa nhân khẩu học của khách hàng, tiếp đến là trực quan tổng quát về phim và hành vi khách hàng để từ đó rút ra được chân dung khách hàng. Cuối cùng, nhóm phân tích về bảng sales, tức trực quan về doanh số bán hàng. Các bước thực hiện như sau:
     -- Dashboard phân tích Nhân khẩu khách hàng, bao gồm:
      Biểu diễn những chỉ số cơ bản: 
      Tổng số khách hàng, Giới tính, Khoảng tuổi, Công việc, Ngành nghề, Biểu đồ tròn về phân bổ địa lí, Tháp tuổi theo giới tính
      Biểu đồ cột thống kê về một số nhân tố: Quận, Khoảng, Công việc và Ngành nghề. 
     -- Bảng phim và hành vi khách hàng
      Biểu diễn những chỉ số: Tổng phim được chiếu, tổng thể loại phim, số phòng chiếu, loại ghế, và tỉ lệ thành viên.
      Biểu đồ cột chồng về lượt xem theo giới tính, khoảng tuổi và slot type
      Bảng xếp hạng thể loại phim được xem nhiều theo giới tính, khoảng tuổi và slot type.
      Heat map kết hợp giữa khoảng tuổi, giới tính và thể loại phim.
      Tree map về hàng ghế và phòng chiếu.
      Donut chart về tỉ lệ phần trăm phim nội địa/ ngoại địa, slot type và popcorn
     -- Bảng sales doanh thu
      Biểu diễn những chỉ số: Tổng doanh số, tổng số vé, tỉ lệ cách thức mua vé
      Scatter plot giữa điểm imdb và doanh thu 
      Biểu đồ cột thống kê doanh thu theo quận, phim nội/ ngoại, cách thức mua vé, khoảng tuổi.
      Biểu diễn cluster để phát hiện outliers KH6166700, 0001121703, 0000029127.
      Pareto theo phim và thể loại
      Sale trends theo ngày và tuần



