# Error analysis card

## Zone × block

| zone | block | what | count |
|---|---|---|---:|
| center | B4 | BOX_GEOMETRY | 1 |
| center | B4 | SPURIOUS | 4 |
| center | C0 | SPURIOUS | 1 |
| edge | B4 | SPURIOUS | 1 |
| mid | B4 | MISSING | 2 |
| mid | B4 | SPURIOUS | 6 |
| mid | C0 | SPURIOUS | 1 |
| unknown | B4 | DUPLICATE | 1 |
| unknown | B4 | MISSING | 1 |
| unknown | B4 | SPURIOUS | 1 |

## Top defects
- SPURIOUS: 14 (ví dụ frame adasind_258420.jpg)
- MISSING: 3 (ví dụ frame adasind_258420.jpg)
- BOX_GEOMETRY: 1 (ví dụ frame adasind_258420.jpg)

## Phân tích của bạn

Hai bảng trên do `python3 lab11.py card` tính từ `findings.csv`; chạy lại lệnh sẽ cập nhật bảng và giữ nguyên mục này. Viết cho lỗi nổi bật nhất, dẫn frame/`object_ref`.

- Nguyên nhân khả dĩ (`why`) và vì sao bạn nghĩ vậy: `SPURIOUS` nổi bật nhất (14 dòng) nhưng không có một nguyên nhân duy nhất. Ở nhãn người, các ca L4 và L6 của `adasind_258420.jpg` là `E1_annotator_error`: một phần của ThreeWheeler bị nhận thành Bike hoặc bị tách thành box thứ hai. Ở model, M4/M8/M11 cùng frame và M6/M9/M6/M7 ở hai frame còn lại lặp lại nhầm ThreeWheeler thành Truck/Car/Bus; mẫu lặp qua ba frame hỗ trợ giả thuyết `E4_model_domain`, dù chưa đủ để ước lượng tỷ lệ lỗi.
- Cách sửa và ai nhận việc (`owner`): `annotator` rework các box người sai theo R01–R04; bản rework `43D4-7709` đã xóa L4, thêm Pedestrian bị thiếu và xóa L7. `ai_team` nhận escalation cho chuỗi model sai class/đè nhiều class lên cùng ThreeWheeler; trước mắt giữ nhãn L/R có lý do, chưa tự đổi model từ slice ba frame.
- Bằng chứng (ảnh trong `screenshots/`, dòng findings, rule): `submission/screenshots/model_compare-B4-dense.png`; các dòng `adasind_258420.jpg/M4`, `M8`, `M11` và `adasind_310008.jpg/M6`, `M7` trong `findings.csv`; R01 (ngưỡng 40 px), R02 (box theo phần nhìn thấy), R03 (rider) và R04 (ThreeWheeler là class riêng).
