1. Phân tích I/O: Cột D dùng Lookup_value là TRIM($C2), Table_array là DanhMucTacGia!$A$2:$E$1000, Col_index_num là 2; cột E dùng cùng Lookup_value và Table_array, Col_index_num là 4; cột F dùng cùng Lookup_value và Table_array, Col_index_num là 5.

2. Giải pháp: Dùng TRIM để xóa khoảng trắng thừa trong Mã tác giả, dùng dấu $ để cố định vùng tra cứu, dùng FALSE để tìm chính xác và bọc VLOOKUP trong IFERROR để thay lỗi #N/A bằng Chưa cập nhật.

3. Các bước thực hiện: Kiểm tra dữ liệu trong hai sheet; nhập công thức vào D2, E2 và F2; kéo công thức xuống dòng 81; kiểm tra các ô Chưa cập nhật; định dạng cột F theo tiền VNĐ.

4. Công thức ô D2: =IFERROR(VLOOKUP(TRIM($C2),DanhMucTacGia!$A$2:$E$1000,2,FALSE),"Chưa cập nhật")

5. Công thức ô E2: =IFERROR(VLOOKUP(TRIM($C2),DanhMucTacGia!$A$2:$E$1000,4,FALSE),"Chưa cập nhật"); công thức ô F2: =IFERROR(VLOOKUP(TRIM($C2),DanhMucTacGia!$A$2:$E$1000,5,FALSE),"Chưa cập nhật"). Chỉ cần thay Col_index_num vì Mã tác giả, vùng tra cứu và cách xử lý lỗi đều giống nhau.

6. Nếu bỏ dấu $, vùng tra cứu tại D2 là DanhMucTacGia!A2:E1000. Khi kéo xuống D5, vùng sẽ thành DanhMucTacGia!A5:E1003, làm mất các dòng 2, 3 và 4 khỏi vùng tra cứu, khiến một số mã có thể trả về lỗi #N/A.
