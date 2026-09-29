# Quan sát vạch ô đỗ

- Các `parking_line` đã vẽ theo vạch trắng chia ô: ví dụ vạch chéo ở tiền cảnh gần giữa ảnh (từ khoảng x=406, y=652 xuống mép dưới) và vạch chéo dài ở tiền cảnh bên phải (từ khoảng x=697, y=622 về mép phải). Vạch ngang dài ở cuối dãy (xấp xỉ y=542 bên trái đến y=504 bên phải) cũng được giữ vì là vạch sơn liên tục, nhìn thấy rõ và tạo ranh cuối chung của dãy ô; không suy diễn phần khuất ngoài ảnh.
- Không vẽ mép/ranh xa sát hàng cây ở cuối bãi: đó là rìa khu vực đỗ xe, không phải vạch sơn phân chia ô.
- `free_space` phủ phần mặt nhựa đường trống ở tiền cảnh giữa các dãy ô; polygon dừng theo rìa dãy vạch và mép ảnh, không kéo qua các vạch ô đỗ. Phần mặt đường trong vùng này nhìn thấy rõ, không bị xe che.
- Ca chưa chắc cần hỏi người soát: không có.
