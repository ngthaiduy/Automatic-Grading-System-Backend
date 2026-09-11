# Hướng dẫn trải nghiệm — Java OOP Auto Grading

**[Mở web và đăng nhập](https://autograding.103-77-243-209.sslip.io/login)**

## Tài khoản demo công khai

Đây là các tài khoản dùng chung có quyền theo vai trò thật, không phải chế độ chỉ xem. Vui lòng không đổi mật khẩu, khóa tài khoản hoặc xóa kỳ thi mẫu để người tiếp theo vẫn trải nghiệm được. Dữ liệu có thể thay đổi khi người khác cùng sử dụng. Không nhập thông tin cá nhân thật hoặc thông tin thanh toán thật.

| Vai trò | Username | Password |
|---|---|---|
| SYSTEM_ADMIN | `demo.admin` | `AWnZPdoke94bmSNtQZTyNVJc` |
| EXAM_STAFF | `demo.staff` | `nb1k18-2nk_3BsTIE0P3bJG4` |
| LECTURER | `demo.lecturer` | `mYpci83uCW-D-dcYATyX-l77` |
| STUDENT | `se173222` | `aeY53zOmJL9PKlZyyJSEykpC` |
| STUDENT | `se173333` | `YRy1o9dY8reBGPETMcHkRCJn` |
| STUDENT | `se173444` | `hmH08YVS5gUfiJAtPVy1nuQg` |

Đăng xuất trước khi đổi vai trò. Có thể dùng các hồ sơ trình duyệt khác nhau để xem nhiều vai trò đồng thời; các tab cùng hồ sơ dùng chung cookie đăng nhập.

## Trải nghiệm nhanh trong 5 phút

1. Đăng nhập `demo.staff`, mở **Kỳ thi → DEMO - Recruiter Playground → Practice Grading**.
2. Xem đề, 3 câu hỏi, 36 tiêu chí rubric và danh sách 3 bài nộp.
3. Mở kết quả từng bài để xem điểm, test case và giải thích từng tiêu chí.
4. Đăng xuất, đăng nhập `se173333`, mở trang kết quả để xem góc nhìn sinh viên với bài đạt 10/10.
5. Thử `se173222` để xem bài bị trừ điểm, hoặc `se173444` để xem phản hồi khi test case thất bại và phát hiện hardcode.

## Tải đề và bài làm mẫu

Các ZIP dưới đây có thể tải trực tiếp từ GitHub, không cần đăng nhập web. Mở file rồi chọn **Download raw file** nếu GitHub hiển thị trang xem file.

- [Đề TRIAL01 — điểm đã đồng bộ theo rubric](demo/paper-rubric.zip)
- [Bài SE173222](demo/SE173222.zip)
- [Bài SE173333](demo/SE173333.zip)
- [Bài SE173444](demo/SE173444.zip)

Trên web, tài khoản staff có thể tải đề từ block và xuất gói bài nộp. Gói xuất gồm bài làm và kết quả kiểm tra cấu trúc. Sinh viên tải bài của chính mình; không dùng tài khoản sinh viên để xem dữ liệu riêng của người khác.

## Kết quả mẫu đã kiểm tra

| Bài | Điểm / 10 | Test case đạt |
|---|---:|---:|
| SE173222 | 7,77 | 8/9 |
| SE173333 | 10,00 | 9/9 |
| SE173444 | 0,00 | 0/9 |

Chế độ **MODE_3**, điểm ba câu **2,5 / 3,75 / 3,75**. Điểm rubric OOP có trọng số 100%; test case vẫn chạy. Quy tắc không đạt test case nào hoặc phát hiện hardcode có thể đưa điểm câu về 0. Vì vậy điểm cấu trúc ban đầu và điểm cuối có thể khác nhau. Đây là kết quả theo cấu hình demo, không phải điểm đã được giảng viên xác nhận độc lập.

## Kỳ thi riêng để thử chấm và xem kết quả

**DEMO - Recruiter Playground → Practice Grading** là khu vực thực hành trong giao diện hiện tại, dùng cùng đề TRIAL01, 36 tiêu chí rubric và ba bài ZIP ở trên.

1. Đăng nhập `demo.staff`.
2. [Mở block thực hành](https://autograding.103-77-243-209.sslip.io/exam-staff/exams/30a6c5cb-f611-4edb-b6d9-415195084eee/blocks/2a548911-28a4-4154-9a9e-30dc777737e6).
3. Vào danh sách bài nộp, bấm **Chấm tất cả** để chạy chấm lại ba bài có sẵn. Không cần upload lại đề hoặc bài.
4. Đợi tiến độ hoàn tất rồi mở từng kết quả để xem điểm câu, test case và rubric feedback.
5. Đổi sang tài khoản sinh viên tương ứng để xem kết quả cá nhân của kỳ thi này.

Mã học kỳ SU26 dùng làm mã dữ liệu demo riêng. Kỳ thi **DEMO - Trial Test 01** là bộ kết quả tham chiếu; thời gian nhận bài đã kết thúc để tránh trùng lịch với ca thực hành. Không cần sửa/xóa bộ tham chiếu để thử chấm.

## 1. Nhân viên khảo thí — demo.staff

- Xem dashboard, danh sách kỳ thi và block thi.
- Vào kỳ thi thực hành để xem đề, rubric, bài nộp, tiến độ chấm và kết quả chi tiết.
- Tải đề, xuất gói bài làm và xem thống kê.
- Nếu muốn thử từ đầu, tạo kỳ thi/block riêng với tên **TRY - tên của bạn**. Mỗi mã học kỳ chỉ có một kỳ thi và các block không được trùng lịch trên toàn hệ thống; luồng nhanh ở trên không cần tạo thêm kỳ thi. Thiết lập lịch đang mở, chọn MODE_3, upload đề rồi cấu hình/lưu rubric trước khi chấm. ZIP đề không thay thế bước kiểm tra rubric trên hệ thống.
- Dùng tài khoản sinh viên nộp bài vào block mới, sau đó quay lại staff để kích hoạt chấm, chờ hoàn tất và xem kết quả.
- Dùng các ZIP mẫu được cung cấp khi thử chấm.

## 2. Sinh viên — se173222 / se173333 / se173444

- Xem kỳ thi và block có lịch phù hợp.
- Xem/tải bài nộp của mình, xem tổng điểm và chi tiết từng câu.
- Mở test case để đối chiếu đầu ra mong đợi và thực tế; đọc phản hồi rubric.
- Muốn thử nộp mới, dùng block riêng do staff tạo và chọn ZIP tương ứng với tài khoản. Việc nộp phụ thuộc lịch thi và điều kiện của block; bộ mẫu hiện đã có bài nộp.
- Có trang ví và phúc khảo. Chức năng nạp tiền qua nhà cung cấp thật chưa được cấu hình/kiểm thử cho demo.

## 3. Giảng viên — demo.lecturer

- Xem dashboard và danh sách đơn phúc khảo được phân công.
- Khi có đơn đã được staff phân công: mở chi tiết, tải bài, xem yêu cầu, nhập đánh giá và gửi kết quả review.
- Nếu danh sách trống, chưa có đơn được phân công cho tài khoản này; đây không phải danh sách tất cả bài thi.
- Luồng phúc khảo: sinh viên tạo đơn hợp lệ → staff phân công giảng viên → giảng viên review → staff xác nhận kết quả. Luồng này có điều kiện về thời hạn, điểm và phí/số dư; chưa được kiểm thử đầy đủ trên demo và chưa chuẩn bị sẵn đơn phúc khảo.

## 4. Quản trị — demo.admin

- Xem dashboard quản trị, danh sách tài khoản và nhật ký hoạt động.
- Xem cấu hình hệ thống và các chế độ chấm điểm.
- Tài khoản có quyền quản trị thật. Thay đổi cấu hình ảnh hưởng người đang thử web, nên ưu tiên xem cấu hình hiện tại; dùng dữ liệu thử riêng nếu cần trải nghiệm chỉnh sửa.
- Các màn hình cấu hình AI/thanh toán không đồng nghĩa dịch vụ bên ngoài đang hoạt động. Không thêm API key hoặc thông tin thanh toán thật vào demo công khai.

## Phạm vi demo

- Đã kiểm thử qua API: upload đề, lưu rubric, nộp ba bài, chạy chấm, đọc kết quả, tải lại bài và quyền sinh viên xem kết quả cá nhân.
- Frontend và backend đã build; web phục vụ HTTPS trên VPS Ubuntu bằng Docker Compose, Nginx và Caddy; dữ liệu dùng PostgreSQL và MinIO.
- Chưa xác minh đầy đủ: mọi thao tác giao diện, toàn bộ phúc khảo, email, AI bên ngoài và thanh toán thật.
- Kỳ thi thực hành Recruiter Playground hiện kết thúc ngày 12/10/2026. Tạo lịch mới nếu muốn thử nộp sau thời điểm đó.
- Mã Java bài nộp hiện chạy trong container backend, chưa có worker cô lập riêng. Chỉ dùng bài mẫu tin cậy trong demo này.
