# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` |Xe con chở người, thân thấp liền khối (sedan, hatchback, SUV) |Không có thùng hàng riêng, không dài kiểu xe khách |
| `truck` |	Xe chở hàng có cabin tách phía trước và thùng/khoang hàng phía sau |Có thùng hàng rõ rệt, thường cao và dài hơn car |
| `bus` |Xe chở nhiều người, thân dài, nhiều cửa sổ thành hàng, nhiều cửa lên xuống |Dài và cao hơn hẳn car/van |
| `van` |Xe thân hộp kín, một khối, cỡ giữa car và truck |Không có cabin tách khỏi khoang sau|

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Cạnh box chạm điểm ngoài cùng nhìn thấy của thân xe; không gồm mặt đường, bóng đổ, xe bên cạnh.
- Vật thể bị che khuất: Vẫn vẽ box quanh phần nhìn thấy nếu nhận ra được lớp; không đoán phần bị che.
- Vật thể bị cắt bởi rìa ảnh: Box chạm đúng rìa ảnh; không đoán phần ngoài ảnh.
- Vật thể rất nhỏ/mơ hồ: Nếu không xác định chắc lớp thì không tự đoán, ghi vào bảng ca mơ hồ và hỏi giảng viên.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_001` |Xe tải bị xe tải che khoảng một nửa |Vẽ box quanh nửa nhìn thấy, lớp truck |Quy tắc che khuất: box quanh phần thấy, nhận ra lớp thì vẫn gán |
| `drive_005` |Xe con bị cắt ở mép phải ảnh |Box kéo sát mép phải ảnh, lớp car |Quy tắc cắt rìa: box chạm rìa, không đoán phần ngoài |
| `drive_026` |Hai xe đi sát nhau, xe sau chồng lên xe trước nên khó thấy ranh giới |Vẽ hai box riêng, mỗi box quanh phần nhìn thấy của từng xe, không gộp thành một |mỗi xe một box; hai xe chồng nhau thì vẽ hai box trên phần nhìn thấy của từng xe |
