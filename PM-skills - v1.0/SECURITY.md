# Security & data rules

Repo này là **PRIVATE** và chỉ chứa định nghĩa skill (văn bản hướng dẫn) cho PM chuẩn PMP/PMI.

1. **Không commit bí mật**: API key, token, mật khẩu, `.env` (đã chặn trong `.gitignore`).
2. **Không commit dữ liệu thật** của dự án/khách hàng/nhân sự (tên, email, lương, hợp đồng). Dùng dữ liệu giả hoặc ẩn danh. Ví dụ email trong `gherkin-patterns.md` chỉ là dữ liệu test.
3. **Bản quyền PMBOK®**: không commit `pmbok8.pdf` hoặc đoạn trích dài. Chỉ giữ `references/pmbok8-index.md` (mục lục + số trang). Trích PDF ở máy local; diễn giải, trích nguyên văn tối thiểu.
4. **Không dùng trí nhớ cho PMBOK**: tra index → `pdftotext -layout -f X -l Y pmbok8.pdf -`.
5. **Chính xác dữ liệu**: số liệu đầu vào do người dùng cung cấp phải được tính lại bằng công cụ, không ước đoán; thiếu dữ liệu thì hỏi lại.
6. Trước mỗi commit: `grep -rniE "api[_-]?key|secret|token|password" .` và kiểm tra `git status`.
