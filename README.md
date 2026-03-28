# 購物車專案 (Shopping Cart Project)

一個完整的購物網站應用，前端使用 Vue.js 開發，後端使用 Spring Boot 開發，並整合 JWT 認證機制。

## 功能特色

- **用戶認證**: 支援用戶註冊、登入，使用 JWT Token 進行身份驗證
- **產品管理**: 新增、刪除、查詢產品，支持按類別、價格範圍篩選和分頁
- **購物車功能**: 添加商品到購物車、查看購物車、修改商品數量
- **訂單管理**: 創建訂單、查看用戶訂單歷史
- **支付整合**: 整合 Stripe 支付系統
- **響應式設計**: 前端使用 Tailwind CSS 實現美觀的響應式界面

## 技術棧

### 後端
- **框架**: Spring Boot 3.3.2
- **Java 版本**: Java 17
- **資料庫**: MariaDB
- **ORM**: Spring Data JPA (Hibernate)
- **安全**: Spring Security + JWT
- **支付**: Stripe Java SDK
- **建構工具**: Maven

### 前端
- **框架**: Vue.js 3
- **建構工具**: Vite
- **狀態管理**: Pinia
- **路由**: Vue Router 4
- **HTTP 客戶端**: Axios
- **樣式**: Tailwind CSS
- **UI 組件**: Headless UI + Heroicons
- **支付**: Stripe.js

## 系統要求

- Java 17 或更高版本
- Node.js 16 或更高版本
- MariaDB 10.0 或更高版本
- Maven 3.6 或更高版本

## 安裝與設定

### 後端設定

1. **克隆專案**
   ```bash
   git clone <repository-url>
   cd ShoppingCart
   ```

2. **資料庫設定**
   - 安裝並啟動 MariaDB
   - 創建資料庫：`cart_db`
   - 設定環境變數：在專案根目錄創建 `.env` 文件
     ```
     DATASOURCE_PASSWORD=your_database_password
     ```

3. **Stripe 設定** (如果使用支付功能)
   - 在 Stripe 控制台獲取 API 金鑰
   - 設定環境變數：
     ```
     STRIPE_SECRET_KEY=your_stripe_secret_key
     STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
     ```

4. **建構與運行**
   ```bash
   # 使用 Maven 建構
   ./mvnw clean install

   # 運行應用
   ./mvnw spring-boot:run
   ```

   後端服務將在 `http://localhost:8080` 啟動

### 前端設定

1. **進入前端目錄**
   ```bash
   cd shopping_cart_frontend
   ```

2. **安裝依賴**
   ```bash
   npm install
   ```

3. **配置環境變數**
   - 創建 `.env` 文件
     ```
     VITE_API_BASE_URL=http://localhost:8080
     VITE_STRIPE_PUBLISHABLE_KEY=your_stripe_publishable_key
     ```

4. **運行開發伺服器**
   ```bash
   npm run dev
   ```

   前端應用將在 `http://localhost:5173` 啟動

## API 文檔

### 認證 API
- `POST /auth/signup` - 用戶註冊
- `POST /auth/login` - 用戶登入

### 產品 API
- `POST /api/product/` - 新增產品
- `DELETE /api/product/{id}` - 刪除產品
- `GET /api/product/{id}` - 獲取單個產品
- `GET /api/product/` - 按條件篩選產品 (支援分頁)

### 購物車 API
- `GET /api/cart/` - 獲取用戶購物車
- `PUT /api/cart/add` - 添加商品到購物車

### 訂單 API
- `POST /api/order/` - 創建訂單
- `GET /api/order/user` - 獲取用戶訂單

所有受保護的 API 端點都需要在請求頭中包含 JWT Token：
```
Authorization: Bearer <your-jwt-token>
```

## 專案結構

```
ShoppingCart/
├── src/main/java/com/shopping_cart_project/shopping_cart_project/
│   ├── Controller/          # REST 控制器
│   ├── Entity/             # JPA 實體
│   ├── Repository/         # 資料存取層
│   ├── Service/            # 業務邏輯層
│   ├── Config/             # 配置類 (JWT, Security)
│   ├── Request/            # 請求 DTO
│   └── Response/           # 響應 DTO
├── src/main/resources/
│   └── application.properties  # 應用配置
├── shopping_cart_frontend/
│   ├── src/
│   │   ├── components/     # Vue 組件
│   │   ├── router/         # 路由配置
│   │   └── stores/         # Pinia 狀態管理
│   ├── public/             # 靜態資源
│   └── package.json        # 前端依賴
└── pom.xml                 # Maven 配置
```

## 開發與測試

### 運行測試
```bash
# 後端測試
./mvnw test

# 前端測試 (如果有配置)
cd shopping_cart_frontend
npm run lint
```

### 建構生產版本
```bash
# 後端
./mvnw clean package

# 前端
cd shopping_cart_frontend
npm run build
```

## 部署

1. 確保所有環境變數正確設定
2. 建構後端 JAR 文件：`./mvnw clean package`
3. 建構前端：`cd shopping_cart_frontend && npm run build`
4. 部署 JAR 文件到伺服器
5. 將前端 dist 文件夾部署到 Web 伺服器

## 貢獻指南

1. Fork 此專案
2. 創建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交變更 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 開啟 Pull Request

## 授權

此專案採用 MIT 授權 - 詳見 [LICENSE](LICENSE) 文件

## 聯絡資訊

如有問題或建議，請開啟 Issue 或聯絡專案維護者。