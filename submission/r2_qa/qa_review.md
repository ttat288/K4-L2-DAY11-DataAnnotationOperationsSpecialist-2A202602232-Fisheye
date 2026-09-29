# QA review · B4-dense

Mã khóa: 64CD-240D

| frame | object_ref | rule_id | nhận xét |
|---|---|---|---|
| adasind_258420.jpg | L4 | R04 | Box `Bike` L4 phủ phần bánh/đầu của xe ba bánh đã có box `ThreeWheeler` L9; ảnh không cho thấy một xe hai bánh riêng ở vùng này. Ghi finding duplicate/spurious, cần bỏ box L4. |
| adasind_258420.jpg | thiếu tại x≈92–109, y≈792–843 | R01 | Có người đi bộ nhỏ riêng biệt phía sau L8; chiều cao nhìn thấy khoảng 51 px (≥H=40) nhưng chưa có box. Ghi finding missing, cần thêm box theo phần nhìn thấy. |
| adasind_270517.jpg | L7 | R03 | Box `Pedestrian` L7 nằm trên phần gương/thân xe `ThreeWheeler` L6; không thấy người đi bộ độc lập trong vùng này. Ghi finding spurious, cần bỏ box L7. Box L1 `Bike` ở biên phải có `truncated=true` phù hợp R05. |
| adasind_310008.jpg | L1–L5 | R01 | Bốn người đi bộ nhìn thấy được tách box; xe ba bánh L5 được gán `ThreeWheeler` và bám phần xe nhìn thấy. Không ghi finding cho frame này. |

Ghi finding r2_qa: cell=L_only, rule_id có giá trị, why để trống.
