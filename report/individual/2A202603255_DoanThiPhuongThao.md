# Báo cáo cá nhân — Ngày 2 Object Detection

Đổi tên file theo `MSSV_HoTen.md`, ví dụ `20241234_NguyenVanAn.md`. Điền kết quả thật, xóa dòng hướng dẫn khi nộp. Xem [quy định nộp](../../SUBMISSION.md).

## 1. Thông tin học viên

- Họ tên: Doãn Thị Phương Thảo
- MSSV: 2A202603255
- Email: dthao18102004@gmail.com
- Lớp: L2B
- Link repo bài làm: https://github.com/dpthao1810/K5-L2B-DAY02-DoanThiPhuongThao-2A202603255-ObjectDetection.git
- Link Colab đã chạy: https://colab.research.google.com/drive/15HK7kP8kWhfm6RUifJYnd9BGaV2mIvG8?usp=sharing

## 2. Schema và mini guideline

Dẫn tới [GUIDELINE_MINI.md](../../GUIDELINE_MINI.md). Tóm tắt ba ca mơ hồ đã quyết định, cách áp dụng schema và phần cần giảng viên làm rõ.

## 3. Annotation và self-QC

- Số file nhãn train: 50
- Kết quả checker và lỗi đã xử lý: Không còn lỗi
- Danh sách ít nhất 10 ảnh đã rà bằng mắt: drive_001.png, drive_002.png, drive_003.png, drive_004.png, drive_005.png, drive_006.png, drive_007.png, drive_008.png, drive_009.png, drive_010.png
- Lỗi bỏ sót/box/class phát hiện khi rà và cách sửa: Phát hiện bỏ sót 2 xe car ở xa, đã bổ sung box
- Commit khóa nhãn ban đầu: b7d912c

## 4. Gold QC và rework

| Chỉ số | Trước sửa | Sau sửa nếu có |
|---|---:|---:|
| TP |26 | |
| FP | 38| |
| FN |87 | |
| Precision |0.406 | |
| Recall |0.233 | |
| F1 |0.296 | |
| mean_iou_of_matches |0.615 | |
| passed |false | |

Dẫn tới `outputs/annotation_evaluation.json` trong repo. Nếu rework, ghi ảnh, lỗi đã kiểm, quyết định sửa/giữ và lý do. Không suy nguyên nhân chỉ từ FP/FN. Không có rework thì ghi rõ.

## 5. Kết quả YOLO

- Runtime, GPU/CPU, phiên bản Ultralytics và Torch: Python 3.13.16, PyTorch 2.14.1+cu130, GPU Tesla T4 (CUDA:0).
- Các tham số thay đổi so với notebook nếu có và lý do: Giữ nguyên các tham số mặc định của bài lab (epochs, imgsz, batch size) để đánh giá baseline.
- Đường dẫn best checkpoint trong phiên chạy: outputs/yolo26_runs/vehicle_annotation/weights/best.pt

| Chỉ số trên 10 ảnh eval | Giá trị |
|---|---:|
| Precision |0.406 |
| Recall |0.233 |
| mAP50 |0.274 |
| mAP50–95 |0.203 |

Đặt cả 2 folder `assets/eval_predictions/` và `assets/yolo26_runs/` (giải nén từ `day2_colab_outputs.zip`) cạnh báo cáo và dẫn link tương đối. Không chỉ ghi số; chỉ ra ít nhất một ảnh và vật thể cụ thể.
Dự đoán eval: "report\individual\assets\eval_predictions"
Luồng chạy YOLO: "report\individual\assets\yolo26_runs"
Trong tập 10 ảnh eval, mô hình hoạt động tốt nhất ở lớp car (Precision 0.836, mAP50 0.741), nhưng nhận diện rất kém ở các lớp thiếu mẫu như bus và van. Nhìn vào ảnh dự đoán report\individual\assets\eval_predictions\visuals\drive_051.jpg, các xe ô tô con cận cảnh được khoanh box chính xác, trong khi các xe van bị bỏ sót (FN) hoặc đoán nhầm thành car.

Trả lời bốn câu hỏi cuối notebook:
1. Lớp nào có recall thấp nhất? Chỉ ra một ảnh eval minh họa. Lớp bus có Recall thấp nhất, bằng 0%. Ảnh drive_058.
2. Nếu mAP50 cao nhưng mAP50-95 thấp, box đang gặp vấn đề gì? ounding box có thể chưa ôm sát đối tượng, bị lệch vị trí hoặc chưa chính xác về chiều rộng và chiều cao.
3. Có lỗi truck/bus/van/car nào liên quan tới guideline không? Nhầm xe van với xe con chỉ vì kích thước hoặc góc nhìn.
4. Vì sao không dùng 10 ảnh eval để train dù chúng có nhãn? Vì mục đích của tập eval là đánh giá khả năng nhận diện và mức độ tổng quát hóa của mô hình trên dữ liệu mà mô hình chưa được huấn luyện.

## 6. Khó khăn và cách xử lý

| Bước/thời điểm | Lỗi quan sát | Cách đã thử | Kết quả/còn thiếu |
|---|---|---|---|
|Gán nhãn van |Dễ nhầm với car và truck |Xem lại GUIDELINE_MINI.md |Đã thống nhất quy tắc phân loại dựa trên chiều cao và thùng xe |

## 7. Tự đánh giá theo rubric

Đối chiếu [RUBRIC.md](../../RUBRIC.md): phần nào đã có kết quả, phần nào còn thiếu hoặc chưa kiểm được. Không tự nhận hoàn thành bước chưa chạy.
[x] Đã hoàn thành gán nhãn tập train và self-QC.
[x] Đã xuất và lưu file đánh giá Gold QC (annotation_evaluation.json).
[x] Đã huấn luyện YOLO, thu được weight best.pt và các chỉ số eval.
[x] Đã hoàn thành trả lời đầy đủ 4 câu hỏi lý thuyết của notebook.

## 8. Công cụ AI và tài liệu tham khảo

Ghi công cụ đã dùng, dùng ở bước nào và phần đã tự kiểm tra; không dùng thì ghi rõ. Liệt kê nguồn ngoài repo được sử dụng. Không ghi mật khẩu/token hoặc đính kèm gold train.
ChatGPT / Gemini hỗ trợ phân tích log Ultralytics, giải thích các chỉ số mAP50-95 và định dạng báo cáo Markdown. Đã tự kiểm tra và đối chiếu toàn bộ số liệu log gốc.
Tài liệu tham khảo:
- Document chính thức của Ultralytics YOLO: https://docs.ultralytics.com/
- Guideline nội bộ bài lab

