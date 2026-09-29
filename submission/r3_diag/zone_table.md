# Zone table (slice của bạn)

Lệnh `python3 lab11.py model` tự ghi bảng số (cùng cách đếm với `r1_craft/compare.md` và `model_compare.md`); chạy lại lệnh sẽ cập nhật bảng và giữ nguyên phần nhận xét. Bạn chỉ viết mục Nhận xét.

| Zone | n_ref | L missing | L spurious | M missing (`LR_noM` + `R_only`) | M thừa (`LM_noR` + `M_only`) | Lỗi L chính (`what`) |
|---|---:|---:|---:|---:|---:|---|
| center | 6 | 1 | 1 | 4 | 5 | BOX_GEOMETRY (1) |
| mid | 7 | 1 | 4 | 1 | 8 | SPURIOUS (4) |
| edge | 7 | 0 | 0 | 1 | 1 | — |

## Nhận xét

- Với người gán nhãn (L), `mid` gãy nhiều nhất: 1 box thiếu và 4 box thừa; `center` có 1 thiếu, 1 thừa, còn `edge` không có thiếu/thừa ở ngưỡng IoU 0.5. Với model (M), `mid` cũng có nhiều lỗi hiện diện nhất (1 thiếu, 8 thừa), kế đến `center` (4 thiếu, 5 thừa); `edge` chỉ có 1 thiếu và 1 thừa.
- Ảnh gốc và các xung đột cho thấy nhiều box thừa ở `mid` đến từ việc tách một ThreeWheeler thành nhiều phần hoặc nhầm phần xe/gương thành object độc lập. Model còn lặp mẫu nhầm ThreeWheeler thành Car/Truck/Bus ở cả ba frame; méo fisheye và box lớn/lỏng có thể góp phần, nhưng đây mới là giả thuyết cần kiểm trên tập lớn hơn. Slice chỉ có ba frame và teaching reference chưa phải gold set, nên bảng này chỉ định vị ca cần soi, không ước lượng tỷ lệ lỗi toàn dữ liệu.
