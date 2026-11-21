# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Nguyễn Đức Cường (`nguyenduccuong`)        Người kiểm (học viên): Đỗ Huy Kiên (`dohuykien`)  
Ngày: 2026-11-21                          Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `nguyenduccuong-front.zip`, `nguyenduccuong-fisheye.zip` (revision 1)  
Số ảnh kiểm: 6 (A01, A04, A07, A08, B01, B06)   Số nhãn đã kiểm (shape + tag): 93 (69 shapes + 24 tags)  

## Tổng hợp theo mã
| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 24 | 1 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 12 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 26 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 26 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 26 | 1 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 26 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 16 | 1 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 16 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 22 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 6 | 1 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 15 | 1 | chính |
| QC1-12 file | lỗi file | 2 | 0 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)
| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-01 | B01_02688_FV.png | tag:camera | nặng | Tag camera đang để giá trị mặc định là `front`, đúng theo tên file `_FV` phải là `fisheye_front` |
| 2 | QC1-05 | A04_b7a8e795-0ff55db2.jpg | lane (L1) | chính | Vạch đứt L1 bị ngắt thành 2 polyline rời rạc; guideline yêu cầu dùng 1 polyline duy nhất nối xuyên suốt |
| 3 | QC1-07 | A07_b41ace08-c8468690.jpg | drivable (direct) | chính | Polygon drivable bị vẽ tràn lấn lên phần bó vỉa lề đường phía bên trái khoảng 10 px |
| 4 | QC1-10 | A08_c0deebc1-16cfa791.jpg | traffic_sign | chính | Hộp bounding box của biển báo phía trên chưa ôm sát viền mép, bao trùm cả một đoạn cột treo |
| 5 | QC1-11 | B01_02688_FV.png | lane (R1) | chính | Vạch sơn trên ảnh mắt cá chỉ có 2 điểm nối thẳng, chưa đặt điểm uốn theo cung cong quang học (lệch tâm > 5 px) |
| 6 | QC1-01 | A01_bc5fadac-fa6dd225.jpg | tag:weather | nhẹ | Thiếu tag weather trên ảnh A01 (chưa gán tag thời tiết) |

## Ca mơ hồ
| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A07_b41ace08-c8468690.jpg | Mép bên trái làn direct chỉ có gờ bê tông bó vỉa, không có sơn trắng thì có tính là thiếu L1 không? | Coach xác nhận đường không có vạch sơn thì không vẽ L1, gán road_curb và được miễn trừ QC1-02. |

## Quyết định
Lỗi nặng: 1   Lỗi chính: 4 / 93 nhãn = 4.3 %   Lỗi nhẹ: 1   Ca chờ lead: 0  
Quyết định (Release / Hold / Rework): **Rework**  
Lý do (theo luật của phiếu): Mặc dù tỷ lệ lỗi chính đạt yêu cầu (4.3 % <= 5.0 %), nhưng lô có 1 lỗi NẶNG tại ảnh B01 (mã QC1-01: tag camera chọn sai giá trị). Theo luật nghiệm thu của Guideline Road v1.0, có ít nhất 1 lỗi nặng bắt buộc phải kết luận **Rework** để học viên sửa lại và nộp bản Revision 2.  

---
*Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).*
