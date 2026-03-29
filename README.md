# 購物車專案 (Shopping Cart Project)

一個完整的購物網站應用，前端使用 Vue.js 開發，後端使用 Spring Boot 開發，並整合 JWT 認證機制。

## 功能特色

- **用戶認證**: 支援用戶註冊、登入，使用 JWT Token 進行身份驗證
- **產品管理**: 新增、刪除、查詢產品，支持按類別、價格範圍篩選和分頁
- **購物車功能**: 添加商品到購物車、查看購物車、修改商品數量
- **訂單管理**: 創建訂單、查看用戶訂單歷史

## 技術棧

### 後端
- **框架**: Spring Boot 3.3.2
- **Java 版本**: Java 17
- **資料庫**: MariaDB
- **ORM**: Spring Data JPA (Hibernate)
- **安全**: Spring Security + JWT
- **建構工具**: Maven

### 前端
- **框架**: Vue.js 3
- **建構工具**: Vite
- **狀態管理**: Pinia
- **路由**: Vue Router 4
- **HTTP 客戶端**: Axios

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

3. **建構與運行**
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
