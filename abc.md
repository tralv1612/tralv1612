```mermaid
graph TD
    subgraph "Giai đoạn 1: Xác thực & Lấy Token Ngắn hạn (Frontend)"
        A[👨‍💻 Người dùng] -->|1. Nhấn nút &quot;Đăng nhập&quot;| B(🌐 Frontend - Trình duyệt);
        B -->|2. Gọi Facebook SDK| C[☁️ Facebook Server];
        C -->|3. Mở Popup Đăng nhập & Xin quyền| A;
        A -->|4. Đồng ý cấp quyền| C;
        C -->|5. Trả về Token Ngắn hạn (User Access Token)| B;
    end

    subgraph "Giai đoạn 2: Đổi Token & Lấy Dữ liệu (Backend)"
        B -->|6. Gửi Token Ngắn hạn đến Backend| D(⚙️ Backend - Server của bạn);
        D -->|7. Gửi Token Ngắn hạn + App Secret| C;
        C -->|8. Trả về Token Dài hạn (User Access Token)| D;
        D -->|9. Dùng Token Dài hạn gọi API lấy Pages| C;
        C -->|10. Trả về Danh sách Pages (chứa Page Access Token)| D;
    end

    subgraph "Giai đoạn 3: Lưu trữ & Hoàn tất"
        D -->|11. Xử lý & Bóc tách dữ liệu| E[💾 Cơ sở dữ liệu];
        E -->|12. Lưu trữ các thông tin quan trọng| E;
        D -->|13. Gửi tín hiệu thành công về Frontend| B;
        B -->|14. Hiển thị thông báo &quot;Hoàn tất!&quot;| A;
    end

    style A fill:#e3f2fd
    style B fill:#e3f2fd
    style D fill:#e8f5e9
    style E fill:#e8f5e9
```
