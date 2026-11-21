# Báo cáo cá nhân — Ngày 11
Họ tên: Phạm Văn Dương      
Mã học viên: 2A202603332    
Phiên bản CVAT (Help → About):  2.81.0  
Guideline: Road v1.0    Lần nộp (`revision` trong manifest): 1  
Thời điểm export (ngày giờ trên CVAT): 10:20 ngày 21/11/2026    
Số lần nộp lại sau Rework:  0

## 1. Kiểm project

| Mục | Đúng như guideline Road v1.0? | Ghi chú |
| :--- | :--- | :--- |
| 6 label, đúng kiểu | Có | `lane` (Polyline), `road_curb` (Polyline), `crosswalk` (Polygon), `drivable` (Polygon), `traffic_light` (Rectangle), `traffic_sign` (Rectangle). |
| Thuộc tính và giá trị | Có | Sử dụng đúng các thuộc tính và giá trị được quy định trong guideline. |
| 4 tag ảnh | Có | `camera`, `timeofday`, `weather`, `source`. |
| Cách kết thúc polyline trên bản CVAT này: | Có | Sử dụng phím tắt `N` để kết thúc polyline. |
| Cách đặt tag ảnh trên bản CVAT này: | Có | Thêm tag trong khu vực Tags của giao diện CVAT, ở cấp ảnh. |


## 2. Số lượng đã gán

| Task | Ảnh | lane | road_curb | crosswalk | drivable | traffic_light | traffic_sign |
| :--- | --: | --: | --: | --: | --: | --: | --: |
| front | 12 | 36 | 23 | 6 | 26 | 37 | 28 |
| front-extra (đã làm 4 / 4) | 4 | 11 | 6 | 4 | 9 | 13 | 13 |
| fisheye | 8 | 10 | 19 | 13 | 14 | 2 | 6 |
| fisheye-extra (đã làm 4 / 4) | 4 | 0 | 9 | 6 | 7 | 0 | 0 |


## 3. Bảng ca khó
| Ảnh | Nhãn | Phân vân giữa | Đã chọn | Lý do |
| --- | --- | --- | --- | --- |
| A01 | lane (L2) | Hai polyline cùng position do vạch đứt bị tách hay là vạch đôi | Giữ nguyên hai polyline | Đây là vạch đôi, không phải vạch đứt bị tách. |
| A04 | lane (L1) | Hai polyline cùng position do vạch đứt bị tách hay là vạch đôi | Giữ nguyên hai polyline | Đây là vạch đôi, không phải vạch đứt bị tách. |
| A06 | lane (L1) | Hai polyline cùng position do vạch đứt bị tách hay là vạch đôi | Giữ nguyên hai polyline | Đây là vạch đôi, không phải vạch đứt bị tách. |
| A11 | lane (L1) | Hai polyline cùng position do vạch đứt bị tách hay là vạch đôi | Giữ nguyên hai polyline | Đây là vạch đôi, không phải vạch đứt bị tách. |
| A14 | lane (L1) | Hai polyline cùng position do vạch đứt bị tách hay là vạch đôi | Giữ nguyên hai polyline | Đây là vạch đôi, không phải vạch đứt bị tách. |
| A16 | lane (L1) | Hai polyline cùng position do vạch đứt bị tách hay là vạch đôi | Giữ nguyên hai polyline | Đây là vạch đôi, không phải vạch đứt bị tách. |

## 4. Phiếu QC 1 nhận được
Bạn kiểm lô của tôi:  Quyết định nhận được:  
| Mã lỗi | Số lỗi | Đồng ý? | Đã sửa? |
| --- | ---: | --- | --- |
|QC1-03 – Lane ở camera hai bên chưa đặt position = other|5|Có|Có|

## 5. Kiểm file export

| File | Mở lại được? | Số shape ảnh 1 (job / file) | Số shape ảnh 2 (job / file) | Tag camera có trong XML? |
|---|---|---|---|---|
| phamvanduong-front.zip | Có | 11 / 11 | 8 / 8 | Có (16 tag) |
| phamvanduong-fisheye.zip | Có | 6 / 6 | 8 / 8 | Có (12 tag) |

## 6. Ảnh chụp màn hình
1. Tab Labels của project:  
   ![Tab Labels của project](<./Ảnh chụp màn hình/tab_labels.png>)
2. Một ảnh camera trước đã gán đủ (làn, vùng lái, đèn/biển):  
   ![Ảnh camera trước đã gán](<./Ảnh chụp màn hình/camera_truoc.png>)
3. Một ảnh fisheye đã gán, phóng to đoạn polyline cong:  
   ![Ảnh fisheye với polyline cong](<./Ảnh chụp màn hình/fisheye_line.png>)
4. Một đoạn XML có `<polyline label="lane">`:  
   ![Đoạn XML có polyline lane](<./Ảnh chụp màn hình/file_xml.png>)

## 7. Tự đánh giá
### Lỗi bạn mắc nhiều nhất hôm nay (theo mã QC1-xx), và cách tránh ở Ngày 20:  

Lỗi xuất hiện nhiều nhất trong kết quả lint là **QC1-03 (7 cảnh báo)** – camera hai bên: lane phải có position = other. Để tránh lỗi này ở Ngày 20, tôi sẽ quan sát kỹ ảnh và đọc kỹ guideline trước khi gán nhãn.

### Nhãn của bạn đi vào model ở đâu?

Nhãn annotation được sử dụng làm ground truth trong quá trình huấn luyện model. Model học mối liên hệ giữa hình ảnh đầu vào và các nhãn do người gán, từ đó dự đoán đối tượng và thuộc tính trên hình ảnh mới.

### Chọn một lỗi đã sửa và nói nó làm model học sai thế nào

Một lỗi tôi đã sửa là QC1-03: gán sai thuộc tính `position` cho lane trong ảnh camera hai bên.

Theo guideline, lane ở camera fisheye trái và phải phải có `position = other`. Nếu gán nhầm thành L1, R1, L2 hoặc R2, model có thể học sai mối liên hệ giữa góc nhìn camera và vị trí của vạch làn. Điều này có thể khiến model dự đoán sai thuộc tính `position` khi gặp những hình ảnh tương tự.


## 8. (Tùy chọn, buffer) Từ polyline đến đích row-anchor
| y | 720 | 680 | 640 | 600 | 560 |
| --- | ---: | ---: | ---: | ---: | ---: |
| x của chúng tôi |  |  |  |  |  |
| x của bạn kia |  |  |  |  |  |

Trả lời 3 câu:

1. Năm số x đó chính là đích mà một model row-anchor học cho vạch này. Nếu bạn dừng polyline sớm 40 px, hàng nào đổi thành "không có làn"?
2. So với bạn được kiểm (cùng ảnh): ở hàng 720 và hàng 560, hai bạn lệch nhau bao nhiêu pixel? Lệch ở hàng nào ảnh hưởng LKA nhiều hơn (slide 25)?
3. Nếu polyline vẽ từ xa về gần (ngược quy tắc 2), cách tính trên có đổi không? Script nào sẽ gặp khó?
