# Phiếu QC 1 — Road v1.0

Lô được kiểm (học viên): Phạm Hải (2A202604047)  
Người kiểm (học viên): Phạm Văn Dương 
Ngày: 21/11/2026  
Phiên bản guideline: Road v1.0  
File được kiểm (tên + `revision` trong manifest): `phamhai-front.zip`, `phamhai-fisheye.zip` — revision 1  
Số ảnh kiểm: 6 (A05, A07, A08, A09, B03, B06) + 3 ảnh chỉ kiểm thêm lane (A01, A04, A11)  
Số nhãn đã kiểm (shape + tag): 102 (78 shape, 24 tag; gồm 13 lane ở 3 ảnh kiểm thêm)

## Tổng hợp theo mã

| Mã | Loại lỗi | Số mục kiểm | Số lỗi | Mức |
| --- | --- | ---: | ---: | --- |
| QC1-01 tag camera | sai thuộc tính / bỏ sót | 80 | 0 | nặng |
| QC1-02 đủ L1, R1 | bỏ sót | 8 | 0 | nặng |
| QC1-03 position | sai thuộc tính / thừa | 31 | 0 | nặng |
| QC1-04 tâm vạch, chiều, điểm dừng | sai phạm vi / bỏ sót | 31 | 0 | chính |
| QC1-05 vạch đứt, che | sai phạm vi / sai thuộc tính | 31 | 0 | chính |
| QC1-06 style, color, kind | sai thuộc tính | 31 | 0 | chính |
| QC1-07 vùng lái | sai phạm vi / bỏ sót / thừa | 26 | 0 | chính |
| QC1-08 đèn, màu | bỏ sót / sai phạm vi / sai thuộc tính | 15 | 0 | nặng / chính |
| QC1-09 facing, type, group, biển phụ | sai thuộc tính | 21 | 0 | chính |
| QC1-10 hình in, đủ biển | bỏ sót / sai phạm vi | 6 | 0 | chính |
| QC1-11 fisheye | sai phạm vi / sai thuộc tính | 25 | 0 | chính |
| QC1-12 file | lỗi file | 283 | 1 | nhẹ / nặng |

## Danh sách lỗi (mỗi lỗi một dòng)

| # | Mã | Ảnh | Nhãn (label, id) | Mức | Mô tả ngắn |
| --- | --- | --- | --- | --- | --- |
| 1 | QC1-12 | A08 | `drivable#9`, `alternative` (số thứ tự theo XML) | nhẹ | Hai điểm polygon liên tiếp bị trùng tại `(635.14, 270.65)`. Cần xóa một điểm thừa. |

## Ca mơ hồ

| Ảnh | Câu hỏi cho lead | Lời đáp (nếu có) |
| --- | --- | --- |
| A05 | Không thấy rõ vạch L1/R1. Có được miễn hai cảnh báo QC1-02 không? | Chưa có |
| A07 | Bên trái là mép bê tông, không thấy rõ vạch L1. Có được miễn QC1-02 không? | Chưa có |
| A09 | Mép phải có vạch R1 thật hay chỉ là mép đường? | Chưa có |
| A01, A04, A09, A11 | Lint báo hai lane cùng `position`. Đây là hai nét của vạch đôi, có cần sửa cách biểu diễn không? | Tôi đã vẽ hai nét riêng theo hướng dẫn coach; cần người kiểm đối chiếu trên ảnh. |
| A08 | L1 chuyển từ `solid` sang `dashed`, tôi tách hai đoạn. Cách này có ổn không? | Trên ảnh là cùng một ranh làn nhưng đổi kiểu sơn; tôi giữ hai đoạn. |
| A05 | Polygon `drivable=alternative` bên phải có ăn sang phần xe đỗ/lề không? | Chưa xác nhận |
| B03 | Hai lane gần bó vỉa có chỗ nào thực ra phải là `road_curb` không? | Chưa xác nhận |
| B06 | Các lane có `position=other`, nhưng cần kiểm thêm chúng có đúng là vạch sơn không? | Chưa xác nhận |

## Quyết định

Lỗi nặng: **0 xác nhận** (còn 4 cảnh báo QC1-02 cần hỏi coach)  
Lỗi chính: **0 / 102 nhãn = 0% lỗi đã xác nhận**  
Lỗi nhẹ: **1**  
Ca chờ lead: **8 mục trong bảng trên**  
Quyết định (Release / Hold / Rework): **Hold (tự kiểm)**  
Lý do (theo luật của phiếu): Chưa rõ có thiếu vạch thật ở A05, A07, A09 hay không; A05 và B03 cũng cần kiểm lại theo ảnh. Chưa đủ cơ sở để Release. `QC1-12` được kiểm cấu trúc trên cả 20 ảnh (283 shape và tag), còn tỷ lệ lỗi chính tính theo 102 nhãn đã chọn kiểm. Đây là phiếu kiểm chéo do tôi thực hiện trên lô của Phạm Hải; các ca mơ hồ vẫn chờ lead xác nhận.

Loại lỗi: bỏ sót = thiếu nhãn phải có; thừa = gán cái không phải đối tượng; sai phạm vi = hình lệch, sai chiều, dừng sai chỗ, tràn vùng. Ba loại này theo cách chia lỗi gán nhãn của ISO/IEC 5259-4 (mục 8.4.2); "sai thuộc tính" và "lỗi file" là khóa học thêm. Cách xếp mức: [thang mức lỗi](../docs/qc_severity_road_v1.0.md).
