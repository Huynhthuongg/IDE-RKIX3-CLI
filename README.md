# IDE-RKIX3-CLI
RKIX STUDIO AI

Technical Design Document (TDD)

Version: 1.0
Author: RKIX Team
Status: Draft

---

1. GIỚI THIỆU

RKIX Studio AI là nền tảng phát triển ứng dụng bằng trí tuệ nhân tạo, cho phép người dùng trò chuyện với AI để tạo, chỉnh sửa và triển khai phần mềm trực tiếp trên trình duyệt.

Mục tiêu:

- Thay thế quy trình lập trình thủ công.
- Cho phép AI tự động tạo source code.
- Theo dõi quá trình thực thi theo thời gian thực.
- Xem trước kết quả ngay trong trình duyệt.
- Hỗ trợ nhiều mô hình AI khác nhau.

---

2. KIẾN TRÚC TỔNG THỂ

2.1 Luồng hệ thống

User
↓
Frontend UI
↓
API Gateway
↓
Agent Orchestrator
↓
AI Models
↓
Code Generator
↓
Sandbox Runtime
↓
Build Service
↓
Preview Service

---

3. MODULE CHÍNH

3.1 Authentication Module

Chức năng:

- Đăng nhập Google
- Đăng nhập GitHub
- Quản lý phiên đăng nhập
- Refresh Token
- Logout

Thông tin lưu:

User
├─ id
├─ email
├─ avatar
├─ provider
├─ createdAt

---

3.2 Chat Module

Chức năng:

- Gửi Prompt
- Nhận phản hồi AI
- Upload file
- Đính kèm hình ảnh
- Lưu lịch sử chat

Dữ liệu:

Conversation
├─ id
├─ userId
├─ title
├─ model
└─ messages

Message
├─ role
├─ content
├─ timestamp

---

3.3 AI Gateway

Nhiệm vụ:

- Quản lý API Key
- Chuyển đổi Model
- Quản lý Token
- Retry Request

Model hỗ trợ:

- GPT / Codex
- Claude
- Gemini
- DeepSeek

---

3.4 Agent Orchestrator

Điều phối nhiều AI Agent.

Agent List:

1. Planner Agent
2. Architect Agent
3. Coder Agent
4. Reviewer Agent
5. Builder Agent
6. Tester Agent
7. Deploy Agent

Workflow:

Prompt
↓
Planner
↓
Architect
↓
Coder
↓
Reviewer
↓
Builder
↓
Tester
↓
Deploy

---

4. GIAO DIỆN

4.1 Màn hình Chat

Thành phần:

Sidebar
Conversation List
Message Panel
Prompt Input
Attachment Area

Layout:

┌──────────────┬─────────────────────┐
│ Sidebar      │ Chat Window         │
│              │                     │
│ Project List │ Messages            │
│              │                     │
└──────────────┴─────────────────────┘

---

4.2 Màn hình Build Runtime

Hiển thị:

- Task Queue
- Build Log
- Error Log
- Runtime Status

Layout:

┌─────────────────────────────┐
│ Runtime Status              │
├─────────────────────────────┤
│ Terminal Output             │
│                             │
│ npm install                 │
│ npm run build               │
└─────────────────────────────┘

---

4.3 Màn hình Preview

Hiển thị:

- Mobile Preview
- Tablet Preview
- Desktop Preview

Toolbar:

- Reload
- Open New Tab
- Device Selector

---

5. FRONTEND

Framework:

React + Vite

Structure:

src/
│
├── pages/
│   ├── Chat.jsx
│   ├── Runtime.jsx
│   ├── Preview.jsx
│
├── components/
│   ├── Sidebar
│   ├── ChatPanel
│   ├── PromptBox
│   ├── AgentLogs
│   ├── PreviewFrame
│
├── hooks/
├── services/
├── store/
├── utils/

State Management:

- Zustand

Routing:

- React Router

Styling:

- TailwindCSS

---

6. BACKEND

Framework:

NodeJS + Express

Structure:

backend/
│
├── routes/
├── controllers/
├── services/
├── agents/
├── runtime/
├── sockets/
├── database/
└── server.js

---

7. DATABASE

PostgreSQL

Tables:

users
projects
conversations
messages
agent_tasks
build_logs
deployments

---

8. SANDBOX EXECUTION

Mỗi project chạy trong container riêng.

Container Lifecycle:

Create
↓
Install Dependencies
↓
Run Build
↓
Start Preview
↓
Destroy

Giới hạn:

CPU: 2 Core
RAM: 4GB
Disk: 5GB

---

9. BUILD SYSTEM

Hỗ trợ:

- React
- Vue
- Next.js
- Node.js
- Express

Pipeline:

Clone Source
↓
Install Packages
↓
Run Tests
↓
Build
↓
Preview

---

10. PREVIEW SYSTEM

Preview Server:

preview.rkix.ai/project-id

Tính năng:

- Live Reload
- Hot Reload
- Console Viewer
- Error Overlay

---

11. REALTIME SOCKET

Socket Events:

chat:send
chat:receive

agent:start
agent:update
agent:complete

build:start
build:log
build:success
build:error

preview:ready

---

12. FILE STORAGE

Storage:

uploads/
projects/
artifacts/
exports/

Lưu:

- Images
- Source Code
- Build Outputs
- Logs

---

13. BẢO MẬT

Authentication:

JWT + OAuth

Bảo vệ:

- Rate Limiting
- CSRF Protection
- XSS Protection
- SQL Injection Protection

---

14. ROADMAP

Phase 1

- Login
- Chat
- GPT Integration

Phase 2

- Multi-Agent
- Build Runtime

Phase 3

- Sandbox

Phase 4

- Preview

Phase 5

- Team Collaboration

Phase 6

- Marketplace

---

15. MVP

Chức năng tối thiểu:

✓ Login Google

✓ Login GitHub

✓ Chat AI

✓ Tạo Source Code

✓ Runtime Log

✓ Preview Website

✓ Lưu Project

✓ Xuất Source Code

Mục tiêu MVP:

Tạo một AI IDE hoạt động tương tự Lovable, Bolt hoặc Replit AI với quy trình Chat → Build → Preview hoàn chỉnh.

---

## Static documentation page

This repository now includes a lightweight static documentation page inspired by the clean, code-first layout of [agents.md](https://agents.md/). It summarizes the AndroidX contribution workflow in Vietnamese, including checkout setup, Android Studio launch commands, build/test notes, and Gerrit upload steps.

Open `index.html` directly in a browser, or serve the folder locally:

```bash
python3 -m http.server 4173
```

Then visit `http://localhost:4173`.
