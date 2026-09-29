# Escalation ticket

## Ticket 1

- **Frame:** `adasind_258420.jpg`, object `M4` ở zone `edge` (liên quan L7/R1 ThreeWheeler).
- **Ảnh chụp:** `submission/screenshots/model_compare-B4-dense.png`.
- **Expected impact:** Model gán `Truck` lên ThreeWheeler mà L và R cùng xác nhận; cùng kiểu nhầm còn xuất hiện với `Car`/`Bus` trên cả ba frame. Nếu dùng pre-label này mà không cảnh báo, người gán nhãn có thể giữ sai class hoặc tạo nhiều box chồng cho một vật, làm tăng `SPURIOUS` và nhiễu thống kê theo class/zone.
- **Owner:** `ai_team`.
- **Recommendation:** Lập tập kiểm có adjudication cho ThreeWheeler trên ảnh fisheye, phân tầng theo zone; đo confusion ThreeWheeler↔Car/Truck/Bus và tỷ lệ dự đoán chồng trước khi cân nhắc retrain/threshold/NMS. Trong lúc chưa có kết quả, giữ nhãn người/reference đã kiểm và gắn cảnh báo cho pre-label kiểu này.
