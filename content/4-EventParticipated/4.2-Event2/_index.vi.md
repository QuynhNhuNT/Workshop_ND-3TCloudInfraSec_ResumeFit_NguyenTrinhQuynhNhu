---
title: "Event 2"
date: 2026-05-23
weight: 2
chapter: false
pre: " <b> 4.2. </b> "
---

# Bài thu hoạch "FCAJ Community Day (23/05/2026)"

### Thông tin sự kiện
*   **Tên sự kiện:** FCAJ Community Day
*   **Thời gian tổ chức:** Buổi sáng ngày nghỉ cuối tuần (23/05/2026)
*   **Địa điểm tổ chức:** Tầng 36, tòa nhà Bitexco, số 02 đường Hải Triều, phường Sài Gòn, thành phố Hồ Chí Minh (Tổ chức trực tiếp)
*   **Đơn vị tổ chức:** AWS Study Group phối hợp cùng cộng đồng FCAJ

### Mục đích của sự kiện
*   **Mục tiêu của chương trình:** Không chỉ để nghe hội thảo, mà là nơi để kết nối, giao lưu, và truyền cảm hứng cho nhau (gặp gỡ đối tác hoặc những người bạn mới có cùng chí hướng).
*   **Nội dung chính muốn truyền tải:** Xoay quanh các chủ đề từ AI, Cloud, đến những câu chuyện thực tế được đúc kết từ kinh nghiệm của các chuyên gia trong ngành. Bàn về việc tối ưu hóa cách dùng Prompt, các công nghệ của AWS (như CloudFront), hành trình thi Hackathon, và tư duy xây dựng kiến trúc AI nghiệp vụ (Enterprise grade).
*   **Giá trị dành cho người tham dự:** Giúp người tham dự hiểu rõ sự biến động của thị trường việc làm dưới tác động của AI, cách chuẩn bị nền tảng để không bị đào thải, và trang bị tư duy giải quyết các bài toán thực tế của doanh nghiệp.

### Danh sách diễn giả
*   **Quỳnh Mai** - Vai trò: MC
*   **Nguyễn Gia Hưng** - Chức vụ: Head of Solution Architect (AWS Vietnam), Founder của FCAJ
*   **Tịnh** - Chức vụ: Platform Engineer (Gotam X)
*   **Hải Anh** - Diễn giả từ Pacific Vietnam (Từng trình bày tại AWS Singapore Summit và Silicon Valley)
*   **Thịnh** - Chức vụ: DevOps Engineer (UTM Group) đại diện nhóm Developers trình bày dự án Hackathon
*   **Đức** - Chuyên gia tối ưu hóa Large Language Models (LLM Optimization)
*   **Vy** - Đại diện từ VPBank (Vietnam Prosperity Joint Stock Commercial Bank) trình bày hệ thống Enterprise Multi-Agent

### Nội dung nổi bật
*   **Tổng quan vấn đề:** AI khiến chi phí tạo phần mềm rẻ đi, do đó nhu cầu phần mềm sẽ tăng khủng khiếp, tạo ra rất nhiều việc làm mới trong mảng vận hành (Platform engineering) và sửa lỗi (fix code do AI sinh ra). Một vấn đề khác là việc sinh code bằng AI nhưng thiếu ngữ cảnh sẽ tạo ra rác (ảo giác/hallucination của LLM).
*   **Giải pháp được giới thiệu:** 
    *   Cần thiết lập ngữ cảnh (Context/System Prompt) rõ ràng khi dùng AI, bao gồm: Goal, Persona, Format thay vì chỉ hỏi lan man.
    *   Sử dụng cơ chế Multi-Agent System (Hệ thống đa tác tử) để giải quyết các bài toán phức tạp (như phân tích tín dụng cho Startup) thay vì nhồi nhét mọi thứ vào một con AI duy nhất.
*   **Công nghệ / Dịch vụ / Công cụ:**
    *   **AWS:** CloudFront (Flat-rate pricing, content compression, chống DDoS), AWS Bedrock, EC2, Lambda, VPC.
    *   **AI/LLM:** Amazon Agent platform, Obsidian (để build Second Brain), MCP (Model Context Protocol).
    *   **Khác:** Terraform (Infrastructure as Code - IaC).
*   **Demo hoặc Case Study:** 
    *   *Dự án UTM Morpho:* Demo công cụ dùng 3 AI agents tạo HTML/UI từ hình ảnh và cho phép người dùng kéo thả, chỉnh sửa trực tiếp trên giao diện trong giải Hackathon.
    *   *Demo Tham số LLM:* Chạy so sánh Temperature = 0 trên AWS Bedrock và trên Local để chứng minh rằng ở trên Cloud, câu trả lời của AI vẫn có sự chênh lệch do cơ chế tối ưu hóa suy luận (Inference Optimization).
*   **Điểm đáng chú ý:** Trong môi trường Enterprise (doanh nghiệp), việc tuân thủ bảo mật và đánh giá rủi ro (Guardrails, Security, Audit) là tối quan trọng, quan trọng hơn việc cắm được bao nhiêu công cụ cho AI.

### Những gì học được
*   **Tư duy và phương pháp:** LLM là một "Probabilistic engine" (mô hình xác suất), do đó đừng mặc định nó luôn trả về cùng một kết quả dù có thiết lập Temperature = 0. Đừng để AI "auto-pilot" hoàn toàn mà luôn phải có con người kiểm duyệt (Human in the loop).
*   **Kiến thức kỹ thuật:** Hiểu cách CloudFront tối ưu chi phí thông qua cơ chế gói Flat-rate (trả phí cố định) để tránh bị "bill sốc" do lượng truy cập đột biến hoặc bị tấn công từ chối dịch vụ (DDoS).
*   **Best practices:** Tránh hội chứng "Internet puller" (thấy thư viện hay code gì trên mạng cũng bê nguyên vào dự án mà không hiểu sâu sắc về ngữ cảnh).
*   **Kinh nghiệm thực tế:** Khi đi thi Hackathon, việc có quá nhiều ý tưởng (over-generation) sẽ làm mất thời gian. Cần giới hạn phạm vi (scope), tập trung vào giải quyết một vấn đề cốt lõi nhất (như tăng cường trải nghiệm biên tập) để kịp hoàn thành sản phẩm trong vòng 36 tiếng.

### Ứng dụng vào công việc
*   **Áp dụng cho dự án hiện tại:** Thiết kế hệ thống AI theo chuẩn Multi-agent: giao việc cụ thể cho từng agent chuyên biệt (ví dụ: Agent phân tích tài chính, Agent nghiên cứu thị trường). Xây dựng mTLS và VPC Origin để bảo mật tài nguyên tối đa.
*   **Công nghệ muốn thử nghiệm:** Áp dụng Terraform để triển khai hạ tầng bằng code (IaC) giúp quản lý phiên bản dễ dàng. Thử nghiệm các tính năng bảo vệ biên của AWS CloudFront (chặn địa lý, block bot tự động).
*   **Ý tưởng cải thiện quy trình làm việc:** Thay vì tải dữ liệu thủ công, có thể dùng AI Agent tích hợp với thư viện (như MCP kết nối Excel) để nó tự động tạo dashboard phân tích hoặc tóm tắt nội dung cuộc họp.

### Trải nghiệm trong event
*   **Học hỏi từ diễn giả:** Nhận ra rằng khi đi làm, nhà tuyển dụng không chỉ hỏi bản demo mà sẽ đào sâu vào tính thực tế của "Sản phẩm" (Product) và các Use case nghiệp vụ thực tiễn.
*   **Trải nghiệm thực hành:** Xem trực tiếp demo xây dựng ứng dụng trong 36 giờ, và xem minh họa trực quan sự khác biệt của LLM khi chạy local so với cloud.
*   **Giao lưu và kết nối:** Khuyến khích sự tự tin, dám đứng lên trình bày (từ các bạn sinh viên đến các diễn giả lớn) vì tỷ lệ chọi khi xin việc thực tế là cực kỳ khốc liệt.
*   **Điều ấn tượng nhất:** Quan điểm cảnh tỉnh mạnh mẽ về việc sao chép nguyên code từ ChatGPT dán vào hệ thống doanh nghiệp sẽ gây họa lớn (phá hỏng coding standard, tạo lỗ hổng bảo mật nghiêm trọng).

### Bài học rút ra
*   **Kiến thức quan trọng nhất:** Kiến thức nền tảng (Foundation), bằng đại học, và các kỹ năng phát triển phần mềm cơ bản (Software Engineering) vẫn là bắt buộc. AI chỉ là điểm cộng, không thể thay thế kỹ thuật phần mềm cốt lõi (như biết cách mã hóa/giải mã mật khẩu an toàn).
*   **Kinh nghiệm thực tế:** Để thuyết phục các cấp quản lý phê duyệt ngân sách làm AI, phải chỉ ra được ROI (Tỉ suất hoàn vốn) và các con số tiết kiệm thực tế, *"Numbers speak louder than words"*.
*   **Định hướng phát triển tiếp theo:** Đi sâu vào tìm hiểu AI Mindset và AI Adoption. Luôn nhớ quy tắc khi xây dựng hệ thống: Không chỉ chạy được, mà nó *"phải chạy một cách an toàn, chạy đáng tin cậy và phục vụ người dùng"*. Đọc kỹ tài liệu chính thức (official doc) khi cấu hình tham số AI thay vì nghe theo các nguồn trôi nổi trên mạng.

---

### Một số hình ảnh khi tham gia sự kiện

<div style="display: grid; grid-template-columns: repeat(auto-fit, minmax(300px, 1fr)); gap: 20px; margin-top: 20px;">
  <div>
    <img src="/images/4-EventParticipated/4.2-Event2/event_image1.png" alt="Diễn giả chia sẻ về Context và System Prompt" style="width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.15);" />
    <p style="text-align: center; font-size: 14px; color: #666; margin-top: 8px;">Diễn giả chia sẻ về Context và System Prompt</p>
  </div>
  <div>
    <img src="/images/4-EventParticipated/4.2-Event2/event_image2.png" alt="Giới thiệu chương trình và agenda sự kiện" style="width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.15);" />
    <p style="text-align: center; font-size: 14px; color: #666; margin-top: 8px;">Giới thiệu chương trình và agenda sự kiện</p>
  </div>
  <div>
    <img src="/images/4-EventParticipated/4.2-Event2/event_image3.png" alt="Trình bày về hành trình từ Zero đến Idea Hackathon" style="width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.15);" />
    <p style="text-align: center; font-size: 14px; color: #666; margin-top: 8px;">Trình bày về hành trình từ Zero đến Idea Hackathon</p>
  </div>
  <div>
    <img src="/images/4-EventParticipated/4.2-Event2/event_image4.jpg" alt="Ảnh tập thể các thành viên tham gia FCAJ Community Day" style="width: 100%; height: auto; border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.15);" />
    <p style="text-align: center; font-size: 14px; color: #666; margin-top: 8px;">Ảnh tập thể FCAJ Community Day</p>
  </div>
</div>
