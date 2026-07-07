# Hot Pepper TW (MVP)

台灣在地化美容媒合平台 MVP 起手式，技術棧：Next.js + TypeScript + Tailwind + Prisma + PostgreSQL + Docker。

## 目前已完成（Step 1）

- Next.js + TypeScript + Tailwind 專案初始化
- Prisma + PostgreSQL 基礎設定
- Docker（app + postgres）開發環境
- MVP 核心資料模型：
  - 使用者（含角色）
  - 店家
  - 美容師
  - 服務項目
  - 預約

## 資料模型重點

- `User`：登入主體，包含 `email`、`passwordHash`、`role`
- `Shop`：店家基本資料，關聯 owner
- `Stylist`：美容師資料，可連結 User
- `Service`：服務項目（時長、價格、分類、上下架）
- `Booking`：預約資料（時間區間、狀態、價格快照）

## 本機啟動

1. 安裝依賴

```bash
npm install
```

2. 設定環境變數

```bash
cp .env.example .env
# 修改 DATABASE_URL
```

3. 啟動 PostgreSQL（Docker）

```bash
docker compose up -d db
```

4. 建立資料表與 Prisma Client

```bash
npm run prisma:migrate -- --name init
npm run prisma:generate
```

5. 啟動開發伺服器

```bash
npm run dev
```

## 使用 Docker 啟動 app + db

```bash
docker compose up --build
```

## 下一步（Step 2+）

- 實作註冊 / 登入 / 登出流程
- 店家、美容師、服務、預約 CRUD 頁面與 API
- 預約衝突檢查與時段規則
- 後續擴充：作品集、搜尋、付款
