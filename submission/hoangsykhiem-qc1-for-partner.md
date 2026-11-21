# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): 03270        Người kiểm (học viên): Hoàng Sỹ Khiêm (2A202603244)  
Ngày: 21/11/2026                      Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): 03270.zip (revision 1)  
Số ảnh kiểm: 6 (+ 6 ảnh thêm, ghi riêng: A01–A12)   Số nhãn đã kiểm (shape + tag): 254 (206 shape + 48 tag)  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 48 | 1 | nhẹ |
| QC1-02 đủ L1, R1 | bỏ sót | 24 | 1 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 34 | 3 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 34 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 34 | 2 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 34 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 49 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 45 | 45 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 123 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 78 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 0 | 0 | chính |
| QC1-12 file | lỗi file | 254 | 1 | nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-12 | Cả lô | file (03270.zip) | nặng | File zip chứa thư mục images/ kèm 12 ảnh .jpg (nặng 840KB), vi phạm quy chuẩn nộp không kèm ảnh |
| 2 | QC1-02 | A08_c0deebc1-16cfa791.jpg | lane | nặng | Thiếu vạch L1 (vạch phân làn bên trái xe có thể nhìn rõ nhưng chưa được gán nhãn L1) |
| 3 | QC1-03 | A08_c0deebc1-16cfa791.jpg | lane | nặng | Lộn xộn vị trí làn: vạch bên phải gán L2, vạch bên trái gán R1 và R2 |
| 4 | QC1-03 | A10_b6ff1331-f6d3fba8.jpg | lane | nặng | Vạch phân làn bên trái xe (x: 90–531) bị gán nhầm thành position = R2 |
| 5 | QC1-03 | A12_c0f978fa-9b4e623f.jpg | lane | nặng | Vạch phân làn bên trái xe (x: 0–472) bị gán nhầm thành position = R2 |
| 6 | QC1-08 | A03, A07, A08, A09, A10, A11, A12 | traffic_light (45 box) | nặng | Toàn bộ 45 box traffic_light đều để light color = None, chưa gán màu đang sáng cho đèn hướng về xe (facing: front) |
| 7 | QC1-05 | A08_c0deebc1-16cfa791.jpg | lane | chính | 2 polyline vạch đứt cùng mang nhãn position = R1 (vạch đứt bị tách đôi thay vì vẽ 1 polyline liên tục) |
| 8 | QC1-05 | A03_b1c66a42-6f7d68ca.jpg | lane | chính | Vạch bị xe phía trước che khuất một đoạn nhưng toàn bộ các vạch đều để cờ occluded = 0 |
| 9 | QC1-01 | A03_b1c66a42-6f7d68ca.jpg | tag:timeofday | nhẹ | Tag timeofday chọn nhầm dusk (ảnh thực tế là ban ngày daytime/day) |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05_b2576c8c-2de20b8a.jpg | Đoạn đường đồi núi không có vạch kẻ đường trên thực tế, không thể gán L1/R1. Có được miễn lỗi QC1-02 không? | Được miễn theo Checkpoint 6 nếu đã xác nhận không có vạch sơn trên mặt đường. |

## Quyết định
Lỗi nặng: 5   Lỗi chính: 2 / 254 nhãn = 0.8%   Lỗi nhẹ: 1   Ca chờ lead: 1  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Có các lỗi nặng gồm đóng gói file kèm ảnh (QC1-12), thiếu vạch L1 (QC1-02), gán sai vị trí làn trái/phải (QC1-03), và chưa gán màu đèn giao thông facing front (QC1-08). Cần xuất lại zip không kèm ảnh và sửa các nhãn bị lỗi.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](docs/qc_severity_road_v1.0.md).
