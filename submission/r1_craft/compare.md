# So sánh L với R

Chỉ số L/R là thứ tự box cao ≥ H=40 trong từng frame, theo thứ tự XML; bắt đầu từ 1.
Box L trong ignore_region được báo IGNORE_SCOPE, không tính SPURIOUS.

## adasind_258420.jpg
- L2 mid SPURIOUS
- L4 mid SPURIOUS
- L5+R8 center BOX_GEOMETRY
- L6 mid SPURIOUS
- R7 mid MISSING
## adasind_270517.jpg
- L7 mid SPURIOUS
## adasind_310008.jpg

## Theo zone
| zone | n_ref | matched | missing | spurious |
|---|---|---|---|---|
| center | 6 | 5 | 1 | 1 |
| mid | 7 | 6 | 1 | 4 |
| edge | 7 | 7 | 0 | 0 |
