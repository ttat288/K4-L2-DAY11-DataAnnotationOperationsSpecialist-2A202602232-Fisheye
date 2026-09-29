# Guideline patch

- **Rule mới đề xuất:** **R12 — Không gán bộ phận phương tiện thành object độc lập.** Gương, thân, bánh hoặc phần cabin của một phương tiện không được tạo box `Pedestrian`/`Bike`/phương tiện thứ hai nếu ảnh không cho thấy ranh giới của một object độc lập. Khi một box nhỏ nằm trong hoặc đè lên box phương tiện lớn, người gán nhãn phải soi ảnh gốc và chỉ giữ cả hai nếu chỉ ra được vật riêng; rider ngồi trên xe hai bánh vẫn theo R03.
- **Áp dụng cho:** `Pedestrian`, `Bike` và các class phương tiện, đặc biệt `ThreeWheeler`, ở mọi zone. Ca gốc: Bike L4 đè lên ThreeWheeler L9 trong `adasind_258420.jpg`, và Pedestrian L7 nằm trên gương/thân ThreeWheeler L6 trong `adasind_270517.jpg`.
- **Vì sao luật hiện tại (`docs/02-rules-vi.md`) không đủ:** R03 nói cách gộp rider với xe hai bánh và R04 ánh xạ class phương tiện, nhưng chưa nêu phép kiểm cho box nhỏ đặt trên một bộ phận của phương tiện lớn. Khoảng trống này làm hai lỗi thật có hình thức khác nhau nhưng cùng nguyên nhân lọt qua self-QC.
- **`rules_version` mới:** `v1.0.0` → `v1.1.0`.
- **Hiệu lực từ:** Áp dụng từ vòng gán nhãn kế tiếp sau khi QA duyệt patch; không hồi tố thay đổi teaching reference nếu chưa adjudicate.
