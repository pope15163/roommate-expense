# Roommate Expense Splitter 🏠💰

一個多人室友分帳應用，用於追蹤室友之間的開支和自動結算。

## 功能特性

- ✅ 用戶認證（用戶名/密碼）
- ✅ 記錄開支和收入
- ✅ 自動分帳計算
- ✅ 多人支持
- ✅ 開支分類
- ✅ 結算統計
- ✅ 交易歷史記錄

## 技術棧

### 前端
- React 18
- TypeScript
- Vite
- Tailwind CSS
- Axios

### 後端
- Node.js + Express
- TypeScript
- PostgreSQL
- JWT 認證
- Prisma ORM

## 項目結構

```
roommate-expense/
├── backend/              # Express 後端應用
│   ├── src/
│   │   ├── routes/       # API 路由
│   │   ├── middleware/   # 中間件
│   │   ├── app.ts        # 應用入口
│   │   └── ...
│   ├── prisma/
│   │   └── schema.prisma # 數據庫模型
│   ├── .env.example
│   ├── package.json
│   └── tsconfig.json
├── frontend/             # React 前端應用
│   ├── src/
│   │   ├── pages/        # 頁面組件
│   │   ├── services/     # API 服務
│   │   ├── types/        # 類型定義
│   │   ├── App.tsx       # 主應用
│   │   └── main.tsx      # 入口點
│   ├── package.json
│   └── vite.config.ts
├── docker-compose.yml    # PostgreSQL 容器配置
└── README.md
```

## 快速開始

### 前置要求
- Node.js 18+
- PostgreSQL 12+ 或 Docker
- npm 或 yarn

### 安裝步驟

#### 1. 克隆倉庫
```bash
git clone https://github.com/pope15163/roommate-expense.git
cd roommate-expense
```

#### 2. 設置數據庫 (使用 Docker)
```bash
docker-compose up -d
```

#### 3. 設置後端
```bash
cd backend
cp .env.example .env
npm install
npm run prisma:generate
npm run prisma:migrate
npm run dev
```

#### 4. 設置前端
```bash
cd ../frontend
npm install
npm run dev
```

#### 5. 訪問應用
- 🌐 前端: http://localhost:5173
- 🔌 後端 API: http://localhost:3000
- 🏥 健康檢查: http://localhost:3000/health

## API 文檔

### 認證端點
```
POST /api/auth/register
POST /api/auth/login
```

### 開支管理
```
GET    /api/expenses
POST   /api/expenses
GET    /api/expenses/:id
PUT    /api/expenses/:id
DELETE /api/expenses/:id
```

### 用戶管理
```
GET /api/users
GET /api/users/:id
```

### 結算
```
GET /api/settlements
```

## 環境配置

### 後端 .env 文件
```env
DATABASE_URL=postgresql://roommate_user:roommate_password@localhost:5432/roommate_db
JWT_SECRET=your_super_secret_jwt_key_change_this_in_production
PORT=3000
NODE_ENV=development
```

## 開發命令

### 後端
```bash
cd backend

# 開發模式（熱重載）
npm run dev

# 構建
npm run build

# 運行生產版本
npm start

# 生成 Prisma 客戶端
npm run prisma:generate

# 運行遷移
npm run prisma:migrate

# 打開 Prisma Studio
npm run prisma:studio
```

### 前端
```bash
cd frontend

# 開發模式
npm run dev

# 構建
npm run build

# 預覽構建版本
npm run preview
```

## 項目功能

### 1. 用戶認證
- 註冊新賬戶（用戶名、郵箱、密碼）
- 用戶名/密碼登錄
- JWT 令牌認證

### 2. 開支管理
- 創建新開支
- 選擇支付者
- 選擇分帳人員
- 自動平均分配金額
- 分類管理（租金、食物、水電、娛樂等）
- 查看開支歷史

### 3. 自動結算
- 實時計算每個人的餘額
- 自動生成最少交易方案
- 顯示誰欠誰多少錢
- 交易建議清單

### 4. 儀表板
- 總開支統計
- 人數統計
- 最近開支列表
- 快速導航

## 數據模型

### User
- id (主鍵)
- username (唯一)
- email (唯一)
- password (已加密)

### Expense
- id (主鍵)
- description
- amount
- category
- paidByUserId (外鍵)
- createdAt

### ExpenseShare
- id (主鍵)
- expenseId (外鍵)
- userId (外鍵)
- amount

### Settlement
- id (主鍵)
- fromUserId (外鍵)
- toUserId (外鍵)
- amount
- settledAt (可選)

## 貢獻指南

1. Fork 倉庫
2. 創建特性分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開設 Pull Request

## 許可證

MIT License - 詳見 [LICENSE](LICENSE) 文件

## 常見問題

### Q: 如何重置數據庫？
```bash
cd backend
npm run prisma:migrate reset
```

### Q: 如何改變 JWT_SECRET？
編輯 `.env` 文件並更改 `JWT_SECRET` 的值。

### Q: 前端無法連接到後端？
確保：
1. 後端在 http://localhost:3000 運行
2. 前端配置中的 API URL 正確
3. CORS 已正確配置

## 聯絡方式

如有問題或建議，歡迎：
- 📝 提交 GitHub Issues
- 💬 發起 Discussions
- 📧 聯繫項目維護者

---

**開始使用吧！** 🚀 立即註冊並邀請你的室友加入應用，開始簡化你們的分帳過程！
