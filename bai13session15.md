

### PHẦN 1 – Thiết lập Hybrid Workflow

1. **Sự cố mất file khi laptop hỏng ổ cứng:**
* **Sự cố này sẽ KHÔNG xảy ra.**
* **Vì sao:** Nếu nhóm đã áp dụng đúng Hybrid Workflow (kết hợp lưu trữ cục bộ và tự động đồng bộ - Auto Sync lên Cloud Workspace) từ đầu, mọi thay đổi trên file `Slide_BaoCao.pptx` đều đã được đẩy ngầm lên đám mây theo thời gian thực. Khi máy hỏng, thành viên chỉ cần đăng nhập tài khoản vào một thiết bị khác là có thể tải xuống hoặc tiếp tục chỉnh sửa phiên bản mới nhất mà không bị mất mát dữ liệu.


2. **3 bước thiết lập Auto Sync hướng dẫn nhóm:**
* **Bước 1:** Cài đặt ứng dụng Cloud Workspace (như Google Drive for Desktop / OneDrive) trên máy tính cá nhân.
* **Bước 2:** Di chuyển toàn bộ thư mục làm việc của dự án SmartCampus vào thư mục được chỉ định đồng bộ tự động của ứng dụng.
* **Bước 3:** Kiểm tra biểu tượng trạng thái đồng bộ (dấu tích xanh trên file/thư mục) để xác nhận dữ liệu đã được đẩy thành công lên Cloud.


3. **Thao tác khôi phục tài liệu bị xóa nhầm trang (`BaoCao_CuoiKy_SmartCampus.docx`):**
* Mở file tài liệu trên Google Docs.
* Chọn **Tệp (File)** > **Lịch sử phiên bản (Version history)** > **Xem lịch sử phiên bản**.
* Tìm mốc thời gian 10 phút trước (trước khi bị xóa nhầm), sau đó nhấn nút **Khôi phục phiên bản này (Restore this version)**.


4. **Vấn đề với thư mục `node_modules` và phim 4K:**
* **Đây là các sai lầm:**
* Đồng bộ các file rác, file hệ thống nặng (như `node_modules` chứa hàng vạn file code nhỏ, gây nghẽn và làm chậm tiến trình đồng bộ).
* Đồng bộ tài sản giải trí cá nhân (phim 4K) lên thư mục chung của dự án, làm lãng phí dung lượng lưu trữ Cloud Workspace và vi phạm quy tắc dùng chung tài nguyên nhóm.


* **Cách xử lý đúng:** Thêm `node_modules` vào danh sách ngoại lệ cần bỏ qua (file `.gitignore` hoặc cấu hình exclude của ứng dụng sync); tuyệt đối không đưa file giải trí cá nhân vào thư mục dự án chung.



---

### PHẦN 2 – Phân quyền chia sẻ an toàn

1. **Bảng phân quyền chi tiết cho các file:**

| File | Mức quyền | Phạm vi chia sẻ | Giải thích |
| --- | --- | --- | --- |
| **BaoCao_CuoiKy_SmartCampus.docx** (gửi giảng viên) | **Viewer (Xem)** | **Restricted (Hạn chế)** | Chỉ cấp quyền xem bằng email cụ thể của giảng viên để chấm điểm, ngăn chặn tuyệt đối tình trạng giảng viên vô tình chỉnh sửa đè lên cấu trúc bài làm của nhóm. |
| **Slide_BaoCao.pptx** (cho 5 thành viên) | **Editor (Chỉnh sửa)** | **Restricted (Hạn chế)** | Giới hạn nội bộ 5 thành viên trong nhóm để cùng nhau hợp tác chỉnh sửa nội dung cấp tốc trong 2 ngày tới. |
| **GopY_BanNhap.docx** (gửi anh khóa trên) | **Commenter (Nhận xét)** | **Restricted (Hạn chế)** | Cho phép anh khóa trên để lại ý kiến góp ý, gạch đầu dòng nhận xét trực tiếp trên văn bản mà không làm thay đổi nội dung gốc của nhóm. |
| **ThongTin_CaNhan_NhomVien.xlsx** | **Restricted (Hạn chế)** | **Restricted (Hạn chế)** | Chứa dữ liệu định danh cá nhân nhạy cảm (CCCD, SĐT), bắt buộc giữ trong vòng kiểm soát chặt chẽ của nhóm, không chia sẻ mở rộng. |

2. **Quy tắc Cờ Đỏ Bảo mật với `ThongTin_CaNhan_NhomVien.xlsx`:**
* **Quy tắc Cờ Đỏ Bảo mật:** Dữ liệu thông tin cá nhân (PII) tuyệt đối không được phép mở rộng quyền truy cập ra bên ngoài hoặc công khai.
* **Tại sao không dùng Anyone with the link + Editor:** Sự kết hợp này biến file chứa CCCD, SĐT thành một tài liệu ai cũng có thể truy cập, xem và chỉnh sửa tự do trên internet, dẫn đến nguy cơ rò rỉ dữ liệu cá nhân cực kỳ nghiêm trọng, vi phạm pháp luật về quyền riêng tư.


3. **2 thao tác cấu hình Settings cho file `Slide_BaoCao.pptx` (cấp Editor cho 5 người):**
* Bật tùy chọn: **"Ngăn người chỉnh sửa thay đổi quyền và chia sẻ thêm người mới"** (*Prevent editors from changing permissions and sharing*).
* Cân nhắc bật thêm tùy chọn hạn chế tải xuống/sao chép đối với các thành phần phụ nếu cần kiểm soát chặt chẽ hơn.



---

### PHẦN 3 – Tổ chức giao tiếp nhóm chuẩn doanh nghiệp

1. **3 vấn đề trong đoạn hội thoại Zalo:**
* **No-Hello:** Nhắn tin cụt lủn *"có ai rảnh không"*, *"ơi gì đấy"* thay vì đi thẳng vào vấn đề và nêu rõ bối cảnh công việc.
* **Spam @all giờ khuya (23:47):** Làm phiền không gian nghỉ ngơi của toàn bộ thành viên vào lúc đêm muộn trước ngày deadline, gây áp lực tâm lý không cần thiết cho những ai đã hoàn thành xong phần việc.
* **Tin nhắn không phân luồng (Messy / Lack of threading):** Trộn lẫn các nội dung giải trí (ảnh mèo) và chat phiếm vào chung không gian trao đổi học thuật/công việc, khiến thông tin quan trọng dễ bị trôi đi.


2. **Đề xuất tên Channel/Topic trên Lark/Slack:**
* `#01-thong-bao-chung`: Kênh độc quyền của nhóm để ghim thông báo, deadline và quyết định quan trọng.
* `#02-du-an-smartcampus`: Kênh trao đổi chuyên môn, gửi file tài liệu và cập nhật tiến độ báo cáo của các thành viên.


3. **Viết lại tin nhắn của Lan theo tư duy Asynchronous (Bất đồng bộ):**
> *"Chào mọi người, mình đang làm phần viết code giao diện slide 4 của báo cáo SmartCampus và đang gặp vướng mắc ở lỗi kết nối API. Mình có để đoạn code và hình ảnh lỗi tại đây: [Link file/ảnh]. Bạn nào rảnh qua xem giúp mình với nhé, mình cảm ơn nhiều!"*


4. **Viết lại tin nhắn của Trưởng nhóm lúc 23:47:**
* *Sử dụng tính năng Schedule Send (Hẹn giờ gửi vào 8:00 sáng hôm sau).*
* *Nội dung:*
> "@Nam @Hoa ơi, deadline nộp báo cáo cuối kỳ là ngày mai. Các bạn kiểm tra lại phần nội dung của mình và cập nhật lên file chung trước 12h trưa nay giúp mình nhé. Cảm ơn hai bạn!"





---

### PHẦN 4 – Thông báo tổng hợp

*Tin nhắn gửi lên kênh `#thong-bao-chung`:*

> 📢 **[THÔNG BÁO CẬP NHẬT DỰ ÁN SMARTCAMPUS]**
> Chào cả nhóm, mình đã tiến hành sắp xếp lại không gian làm việc trên Cloud Workspace để chuẩn bị cho hạn nộp báo cáo sắp tới. Cả nhà lưu ý các điểm sau nhé:
> 1. Mình đã thiết lập xong Hybrid Workflow và bật **Auto Sync** cho toàn bộ thư mục dự án lên Cloud để đồng bộ dữ liệu thời gian thực và lưu trữ lịch sử phiên bản phòng ngừa sự cố.
> 2. Đã chia sẻ file `BaoCao_CuoiKy_SmartCampus.docx` cho Giảng viên hướng dẫn theo đúng chuẩn bảo mật (**Viewer / Restricted** - giảng viên chỉ xem để chấm điểm, không lo bị sửa đè nội dung).
> 3. @Nam @Hoa ơi, phần nội dung phụ trách của hai bạn hiện chưa thấy cập nhật trên file chung. Các bạn tranh thủ hoàn thành nốt giúp nhóm trước 12h trưa nay nhé!
> 
> 
> Chúc cả nhà làm việc hiệu quả! 