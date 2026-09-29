# Đề xuất gold set theo camera — tình huống giả lập

**Đầu bài:** 50.000 frame từ bốn camera SVM, ngân sách chọn 200 frame để review/gold. Đây là tình huống trên slide,
**không phải** 50.000 frame có trong repo. Phân bổ đúng 200 ở `45_sampling_plan.csv` cho bốn camera, mỗi camera có
normal và hard slice. “Gold set” ở đây là **kế hoạch tạo** reference sau kiểm chứng, không phải teaching reference
ADASIND hoặc nhãn bạn vừa vẽ. Nếu cần, dùng `notebooks/day11-svm360-colab.ipynb` để thử tổng phân bổ; notebook
không làm thay phần lý do.

| camera_id | Hard case cần chọn | Vì sao dễ sai | Annotation space / calibration cần giữ | Cách review trước khi gọi là gold |
|---|---|---|---|---|
| front | Xe cắt ngang đầu xe; người đi bộ gần xe; vật ở seam trước-trái/phải | Góc nhìn rộng làm méo kích thước; che khuất một phần và vùng seam có thể tạo hai biểu diễn | Giữ hệ tọa độ ảnh fisheye gốc, calibration riêng camera trước, quy tắc H và truncated/occluded nhất quán | Hai annotator gán độc lập; adjudicator xem ảnh gốc, metadata thời gian và calibration; xác nhận chính sách seam trước khi chốt |
| rear | Xe áp sát; xe hai bánh nhỏ; người đi bộ trong thiếu sáng; seam sau | Vật nhỏ, lóa đèn và khoảng cách gây box không ổn định; hai camera có thể cùng thấy một vật | Giữ calibration camera sau, zone riêng theo camera và timestamp đồng bộ; không chuyển tọa độ từ camera khác | Review độc lập các hard case, đối chiếu frame lân cận và thời gian; adjudicate các trường hợp đổi kích thước/visibility |
| left | Xe hai bánh và người đi bộ sát hông; vật bị thân xe che; seam trước-trái/sau-trái | Vật chỉ lộ một phần và vùng mép fisheye méo mạnh; nguy cơ bỏ sót hoặc gán truncated không nhất quán | Giữ image space và calibration trái; ghi rõ occluded/truncated theo phần nhìn thấy, không bù phần khuất | Đối chiếu ảnh gốc và chuỗi thời gian; reviewer thứ hai tập trung vùng sát thân xe và hai seam trái |
| right | Người đi bộ/xe đạp sát lề; xe đỗ; vật đi qua seam trước-phải/sau-phải | Nhiều vật đứng yên cạnh lề; phân biệt vật cần nhãn với nền/đồ vật đường phố có thể khó | Giữ calibration phải, zone camera phải và định nghĩa class thống nhất; không áp chính sách vùng nhìn trái sang phải nếu góc nhìn khác | Lấy mẫu hard độc lập, review vật sát lề và vùng khuất; adjudicator ghi căn cứ ảnh và policy cho các trường hợp mơ hồ |

- Refresh khi thay camera/lens, vị trí lắp, calibration/warp, phiên bản rule hoặc taxonomy; cũng refresh sau khi drift theo camera hoặc nhóm lỗi mới được xác nhận. Giữ phiên bản cũ để so sánh và đánh giá lại tập ảnh bị ảnh hưởng theo kế hoạch migration.
- Ví dụ: một xe máy đồng thời xuất hiện ở seam trước-trái trong camera front và left với hai box khác nhau. Trước khi hợp nhất hay giữ cả hai cần timestamp đồng bộ, calibration/transform hai camera, ảnh gốc của cả hai, định nghĩa identity/track và policy đầu ra của hệ thống; adjudicator ghi quyết định cùng lý do.
- Đồng thuận trên một camera không kiểm tra được độ phủ, méo hình, occlusion, calibration hoặc seam của ba camera còn lại. Quality report đo sự phù hợp với tiêu chí/mẫu đã chọn, không tự chứng minh mẫu đại diện hay nhãn đúng; cần kiểm định độc lập theo từng camera, hard case và seam, cùng adjudication có evidence.
