# Kế hoạch review từ lỗi quan sát được

Từ `findings.csv` và `zone_table.md`, chọn **hai lát cắt của bài ADASIND một camera** cần review trước. Bảng này
giải thích dữ liệu thật bạn vừa làm; nó không thay cho kế hoạch bốn camera giả lập ở `45_sampling_plan.csv`.

| Lát cắt / frame | Số ca và loại lỗi | Vì sao review trước | Bằng chứng cần giữ |
|---|---|---|---|
| `adasind_258420.jpg` — ưu tiên `mid`, sau đó `center` | `mid`: thiếu Pedestrian R7/M12 và nhiều box thừa của L/M; `center`: L5+R8 sai hình học, L6 thừa, M8/M11 sai class | Đây là frame yếu nhất trong local quality (TP=6, FP=4, FN=2; accuracy 0.500) và gom cả lỗi bỏ sót, tách một vật thành hai box, lẫn class ThreeWheeler | Ảnh gốc; `r1_craft/compare.html`; `r3_diag/model_compare.html`; dòng L4, L5+R8, L6, R7+M12, M8, M11 trong findings; R01–R04 |
| `adasind_310008.jpg` — `mid`, object ThreeWheeler L5+R1 | 2 dự đoán model thừa chồng nhau: M6=`Truck`, M7=`Bus`, cùng đè lên một ThreeWheeler | Zone table cho thấy `mid` là vùng có nhiều lỗi nhất; ca này còn chứng minh pattern model nhầm/nhân nhiều class lặp sang frame thứ ba dù nhãn người và reference khớp | Ảnh gốc; `model_compare.html`; dòng M6 và M7 trong findings; R04; giữ tọa độ và class của cả L/R/M |

Giới hạn của kết luận từ ba frame ADASIND: đây chỉ là một slice một camera với ba frame, các frame có thể gần nhau về cảnh và teaching reference chưa phải gold set. Vì vậy số lỗi theo zone/class chỉ dùng để ưu tiên review và tạo giả thuyết; không đại diện cho phân bố toàn bộ ADASIND, bốn camera SVM hay tỷ lệ lỗi sản xuất.

## Chuyển sang kế hoạch bốn camera giả lập

Cách soát độ phủ của 200 frame ở `45_sampling_plan.csv` (kể cả tránh đếm nhiều frame liền nhau trong cùng cảnh
như nhiều ca độc lập), và vì sao kế hoạch đó chỉ giúp tìm ca cần soi, chưa đo được tỷ lệ lỗi: 200 frame được phân tầng đủ `front/rear/left/right × normal/hard`, rải theo chuyến/cảnh/thời điểm và gom các frame liên tiếp của cùng cảnh thành một cụm lấy mẫu để tránh giả độc lập. Phần hard được oversample nhằm tăng khả năng gặp seam, che khuất, méo rìa và vật nhỏ. Vì đây là lấy mẫu chủ đích, không ngẫu nhiên theo xác suất từ 50.000 frame, các quan sát không có trọng số chọn mẫu và các frame cùng cảnh còn tương quan; do đó kế hoạch chỉ tìm ca cần soi/adjudicate, chưa thể suy ra tỷ lệ lỗi hay khoảng tin cậy cho toàn dữ liệu.
