# Social Service Hub Documentation

## Table of Contents
1. [Overview](#1-overview)
2. [Quick Start](#2-quick-start)
3. [Folder Structure & File-by-File Breakdown](#3-folder-structure--file-by-file-breakdown)
4. [Main Features](#4-main-features)
5. [How to Use](#5-how-to-use)
6. [API Documentation](#6-api-documentation)
7. [Testing](#7-testing)
8. [Deployment](#8-deployment)
9. [Development Workflow](#9-development-workflow)
10. [Troubleshooting](#10-troubleshooting)
11. [Performance Considerations](#11-performance-considerations)
12. [Security Considerations](#12-security-considerations)
13. [Contributing](#13-contributing)
14. [License](#14-license)
15. [Supabase Schema and Row Level Security (RLS)](#15-supabase-schema-and-row-level-security-rls)

## 1. Overview

Social Service Hub is a comprehensive, modern admin dashboard built with React, Vite, TypeScript, and Supabase. It provides a robust interface for managing users, services, orders, and transactions, with features like CRUD operations, data filtering and sorting, real-time analytics, and a responsive, mobile-friendly UI.

**Key Technologies:**

*   **Frontend:** React, Vite, TypeScript
*   **Backend & Database:** Supabase
*   **UI Components:** shadcn/ui, Tailwind CSS
*   **Routing:** React Router DOM
*   **State Management:** TanStack Query
*   **Forms:** React Hook Form

## 2. Quick Start

```bash
# Clone the repository
git clone <repository-url>
cd social-service-hub

# Install dependencies
npm install
# or
bun install

# Set up environment variables
cp .env.example .env
# Edit .env with your Supabase credentials

# Start development server
npm run dev
# or
bun run dev

# Open http://localhost:5173 in your browser
```

## 3. Folder Structure & File-by-File Breakdown

This section provides a detailed breakdown of the project's structure and the purpose of each file.

### 3.1. `/` (Root Directory)

*   **`vite.config.ts`**: Vite configuration file. Sets up the development server, plugins (including React and a component tagger for development), and path aliases.
*   **`package.json`**: Defines project metadata, dependencies, and scripts.
*   **`tsconfig.json`**: TypeScript compiler options, including path aliases for cleaner imports.
*   **`tailwind.config.ts`**: Tailwind CSS configuration, including theme customizations and plugins.
*   **`postcss.config.js`**: PostCSS configuration for processing CSS.
*   **`index.html`**: The main HTML entry point for the application.
*   **`README.md`**: Project documentation.

### 3.2. `/src`

This directory contains the core source code of the application.

#### 3.2.1. `/api`

Contains all API functions for interacting with the Supabase backend.

*   **`authApi.ts`**: Handles authentication-related functions:
    *   `login(email, password)`: Signs in a user with email and password.
    *   `register(email, password)`: Creates a new user.
    *   `logout()`: Signs out the current user.
*   **`userApi.ts`**: Manages user-related data.
*   **`orderApi.ts`**: Manages order-related data.
*   **`serviceApi.ts`**: Manages service-related data.
*   **`transactionApi.ts`**: Manages transaction-related data.
*   **`addFundApi.ts`**: Handles wallet and fund management.

#### 3.2.2. `/components`

Contains reusable UI components.

*   **`/shared`**:
    *   **`AdminSidebar.tsx`**: The main sidebar navigation for the admin layout.
    *   **`DashboardCard.tsx`**: A card component used to display statistics on the admin dashboard.
    *   **`LoadingSpinner.tsx`**: A loading spinner component.
    *   **`NavBar.tsx`**: The main navigation bar.
    *   **`ProtectedRoute.tsx`**: A component to protect routes that require authentication.
*   **`/ui`**: Contains [shadcn/ui](https://ui.shadcn.com/) primitive components, which are reusable, accessible, and customizable UI primitives.

#### 3.2.3. `/contexts`

*   **`AuthProvider.tsx`**: A React context provider that manages the application's authentication state, making user information available to all components that need it.

#### 3.2.4. `/hooks`

Contains custom React hooks for shared logic.

*   **`useAuth.ts`**: A hook that provides easy access to the authentication context.
*   **`useDebounce.ts`**: A hook to debounce input, useful for delaying API calls in search and filter inputs.
*   **`use-mobile.tsx`**: A hook to detect if the application is being viewed on a mobile device.
*   **`use-toast.ts`**: A hook for displaying toast notifications.

#### 3.2.5. `/layouts`

*   **`AdminLayout.tsx`**: The main layout for all admin pages, including the `AdminSidebar` and content area.
*   **`MainLayout.tsx`**: The layout for public-facing or user-specific pages.

#### 3.2.6. `/lib`

*   **`supabaseClient.ts`**: Initializes and exports the Supabase client.
*   **`utils.ts`**: Contains utility functions used across the application.

#### 3.2.7. `/pages`

Contains the main pages of the application.

*   **`/admin`**:
    *   **`ControlCenter.tsx`**: The main admin dashboard with key statistics.
    *   **`UserManagement.tsx`**: User management page with CRUD operations.
    *   **`UserDetail.tsx`**: Detailed user information page.
    *   **`OrderManager.tsx`**: Order management page.
    *   **`OrderDetail.tsx`**: Detailed order information page.
    *   **`ServiceManager.tsx`**: Service management page.
    *   **`TransactionManager.tsx`**: Transaction management page.
*   **`/auth`**:
    *   **`LoginPage.tsx`**: User login page.
    *   **`RegisterPage.tsx`**: User registration page.
*   **`/user`**:
    *   **`HomePage.tsx`**: User home page with available services.
    *   **`MyOrdersPage.tsx`**: User's order history page.
    *   **`OrderServicePage.tsx`**: Service ordering page.
    *   **`TransactionPage.tsx`**: User transaction history page.
    *   **`WalletPage.tsx`**: User wallet management page.
*   **`NotFoundPage.tsx`**: 404 error page.

#### 3.2.8. `/types`

*   **`index.ts`**: TypeScript type definitions for the application's data structures.

### 3.3. Main Application Files

*   **`main.tsx`**: The entry point of the React application.
*   **`App.tsx`**: The root component setting up providers and routes.
*   **`index.css`**: Global CSS styles.

## 4. Main Features

*   **User Management**: Full CRUD operations for users with status management and search capabilities.
*   **Service Management**: Comprehensive service management with pagination and status toggles.
*   **Order Management**: Detailed order tracking with status workflows and refund logic.
*   **Transaction Management**: Complete financial transaction records with detailed views.
*   **Admin Dashboard**: Central hub with statistics and insights.
*   **Authentication**: Secure login/registration with protected routes.
*   **Supabase Integration**: Scalable backend with real-time capabilities.
*   **Responsive UI**: Mobile-friendly design with accessibility features.
*   **Wallet System**: Integrated wallet management with balance tracking.
*   **Real-time Updates**: Live data synchronization across all components.

## 5. How to Use

### 5.1. Prerequisites

*   Node.js (version 18 or higher)
*   npm or bun package manager
*   Supabase account

### 5.2. Installation

1. **Clone the repository**:
   ```bash
   git clone <repository-url>
   cd social-service-hub
   ```

2. **Install dependencies**:
   ```bash
   npm install
   # or
   bun install
   ```

3. **Set up environment variables**:
   Create a `.env` file in the root directory:
   ```env
   VITE_SUPABASE_URL=your-supabase-url
   VITE_SUPABASE_ANON_KEY=your-supabase-anon-key
   ```

4. **Set up Supabase**:
   - Create a new Supabase project
   - Run the SQL schema provided in section 15
   - Configure Row Level Security policies
   - Set up authentication providers if needed

5. **Start the development server**:
   ```bash
   npm run dev
   # or
   bun run dev
   ```

6. **Access the application**:
   Open your browser and navigate to `http://localhost:5173`

### 5.3. Default Admin Setup

To create an admin user:
1. Register a new user through the registration page
2. In your Supabase dashboard, update the user's `is_admin` field to `true`
3. The user will now have access to admin features

## 6. API Documentation

### 6.1. Authentication API (`authApi.ts`)

```typescript
// Login user
login(email: string, password: string): Promise<AuthResponse>

// Register new user
register(email: string, password: string): Promise<AuthResponse>

// Logout current user
logout(): Promise<void>

// Get current user
getCurrentUser(): Promise<User | null>
```

### 6.2. User API (`userApi.ts`)

```typescript
// Get all users (admin only)
getUsers(): Promise<User[]>

// Get user by ID
getUserById(id: string): Promise<User>

// Update user
updateUser(id: string, updates: Partial<User>): Promise<User>

// Delete user
deleteUser(id: string): Promise<void>
```

### 6.3. Service API (`serviceApi.ts`)

```typescript
// Get all services
getServices(): Promise<Service[]>

// Create new service
createService(service: CreateServiceRequest): Promise<Service>

// Update service
updateService(id: string, updates: Partial<Service>): Promise<Service>

// Delete service
deleteService(id: string): Promise<void>
```

### 6.4. Order API (`orderApi.ts`)

```typescript
// Get orders for user
getUserOrders(userId: string): Promise<Order[]>

// Create new order
createOrder(order: CreateOrderRequest): Promise<Order>

// Update order status
updateOrderStatus(id: string, status: OrderStatus): Promise<Order>

// Process refund
processRefund(orderId: string): Promise<void>
```

### 6.5. Transaction API (`transactionApi.ts`)

```typescript
// Get user transactions
getUserTransactions(userId: string): Promise<Transaction[]>

// Create transaction
createTransaction(transaction: CreateTransactionRequest): Promise<Transaction>

// Update transaction status
updateTransactionStatus(id: string, status: TransactionStatus): Promise<Transaction>
```

### 6.6. Wallet API (`addFundApi.ts`)

```typescript
// Get user wallet
getUserWallet(userId: string): Promise<Wallet>

// Add funds to wallet
addFunds(userId: string, amount: number): Promise<Transaction>

// Get wallet balance
getWalletBalance(userId: string): Promise<number>
```

## 7. Testing

### 7.1. Running Tests

```bash
# Run all tests
npm test

# Run tests in watch mode
npm run test:watch

# Run tests with coverage
npm run test:coverage

# Run specific test file
npm test -- UserManagement.test.tsx
```

### 7.2. Test Structure

```
src/
├── __tests__/
│   ├── components/
│   ├── hooks/
│   ├── pages/
│   └── utils/
├── __mocks__/
└── test-utils.tsx
```

### 7.3. Testing Guidelines

- Use React Testing Library for component tests
- Mock Supabase client for API tests
- Test user interactions and accessibility
- Maintain test coverage above 80%

## 8. Deployment

### 8.1. Build for Production

```bash
# Create production build
npm run build

# Preview production build locally
npm run preview
```

### 8.2. Deployment Options

#### Vercel (Recommended)
```bash
# Install Vercel CLI
npm i -g vercel

# Deploy
vercel

# Set environment variables in Vercel dashboard
```

#### Netlify
```bash
# Install Netlify CLI
npm i -g netlify-cli

# Deploy
netlify deploy --prod --dir=dist
```

#### Self-hosted
```bash
# Build the project
npm run build

# Serve the dist folder with any static file server
# Example with serve:
npx serve -s dist
```

### 8.3. Environment Variables for Production

Ensure these environment variables are set in your deployment platform:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`

## 9. Development Workflow

### 9.1. Git Workflow

```bash
# Create feature branch
git checkout -b feature/feature-name

# Make changes and commit
git add .
git commit -m "feat: add new feature"

# Push and create pull request
git push origin feature/feature-name
```

### 9.2. Code Style

- Use TypeScript for type safety
- Follow ESLint and Prettier configurations
- Use conventional commits
- Write meaningful component and function names

### 9.3. Development Scripts

```bash
# Start development server
npm run dev

# Type checking
npm run type-check

# Lint code
npm run lint

# Format code
npm run format

# Build project
npm run build
```

## 10. Troubleshooting

### 10.1. Common Issues

#### Supabase Connection Issues
```bash
# Check environment variables
echo $VITE_SUPABASE_URL
echo $VITE_SUPABASE_ANON_KEY

# Verify Supabase project is active
# Check network connectivity
# Validate API keys in Supabase dashboard
```

#### Build Errors
```bash
# Clear node_modules and reinstall
rm -rf node_modules package-lock.json
npm install

# Clear Vite cache
rm -rf node_modules/.vite
npm run dev
```

#### Authentication Issues
- Verify RLS policies are correctly configured
- Check if user has the required permissions
- Ensure auth tokens are not expired

### 10.2. Debug Mode

Enable debug mode by adding to `.env`:
```env
VITE_DEBUG=true
```

### 10.3. Performance Issues

- Check network tab for slow API calls
- Use React DevTools Profiler
- Monitor Supabase dashboard for query performance

## 11. Performance Considerations

### 11.1. Optimization Strategies

- **Code Splitting**: Use dynamic imports for large components
- **Lazy Loading**: Implement lazy loading for images and components
- **Caching**: Utilize TanStack Query for efficient data caching
- **Database Indexing**: Ensure proper indexes on frequently queried columns

### 11.2. Bundle Analysis

```bash
# Analyze bundle size
npm run build
npm run analyze
```

### 11.3. Database Performance

- Use the provided database indexes
- Implement pagination for large datasets
- Monitor query performance in Supabase dashboard
- Use database views for complex queries

## 12. Security Considerations

### 12.1. Authentication Security

- Implement proper session management
- Use secure password policies
- Enable MFA when available
- Regularly rotate API keys

### 12.2. Data Security

- All sensitive data is protected by RLS policies
- Input validation on both client and server
- Sanitize user inputs to prevent XSS
- Use environment variables for sensitive configuration

### 12.3. API Security

- Rate limiting implemented through Supabase
- CORS properly configured
- All API endpoints require authentication
- Admin endpoints have additional authorization checks

## 13. Contributing

### 13.1. Getting Started

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests for new features
5. Ensure all tests pass
6. Submit a pull request

### 13.2. Development Guidelines

- Follow the existing code style
- Write comprehensive tests
- Update documentation for new features
- Use TypeScript for all new code
- Follow the component structure conventions

### 13.3. Pull Request Process

1. Ensure your code follows the style guide
2. Add appropriate tests
3. Update documentation if needed
4. Request review from maintainers
5. Address feedback and merge

### 13.4. Code Review Checklist

- [ ] Code follows style guidelines
- [ ] Tests are included and passing
- [ ] Documentation is updated
- [ ] No breaking changes without discussion
- [ ] Security considerations addressed

## 14. License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### 14.1. Third-Party Licenses

- React: MIT License
- Supabase: Apache License 2.0
- Tailwind CSS: MIT License
- shadcn/ui: MIT License

## 15. Supabase Schema and Row Level Security (RLS)

-- =============================================
-- Admin Service Hub - Supabase Schema và RLS
-- =============================================

-- 1. TẠO CÁC BẢNG CƠ BẢN
-- =============================================

-- Bảng users (mở rộng từ auth.users)
CREATE TABLE public.users (
    id uuid REFERENCES auth.users(id) ON DELETE CASCADE NOT NULL PRIMARY KEY,
    email text UNIQUE NOT NULL,
    full_name text,
    avatar_url text,
    is_admin boolean DEFAULT FALSE NOT NULL,
    status text DEFAULT 'active' CHECK (status IN ('active', 'inactive', 'suspended')),
    created_at timestamp with time zone DEFAULT now() NOT NULL,
    updated_at timestamp with time zone DEFAULT now() NOT NULL
);

-- Bảng services (quản lý dịch vụ)
CREATE TABLE public.services (
    id uuid DEFAULT gen_random_uuid() NOT NULL PRIMARY KEY,
    name text NOT NULL,
    description text,
    price numeric(10,2) NOT NULL CHECK (price >= 0),
    is_active boolean DEFAULT TRUE NOT NULL,
    category text DEFAULT 'general',
    created_at timestamp with time zone DEFAULT now() NOT NULL,
    updated_at timestamp with time zone DEFAULT now() NOT NULL
);

-- Bảng wallets (ví tiền)
CREATE TABLE public.wallets (
    id uuid DEFAULT gen_random_uuid() NOT NULL PRIMARY KEY,
    user_id uuid REFERENCES public.users(id) ON DELETE CASCADE NOT NULL UNIQUE,
    balance numeric(15,2) DEFAULT 0.00 NOT NULL CHECK (balance >= 0),
    created_at timestamp with time zone DEFAULT now() NOT NULL,
    updated_at timestamp with time zone DEFAULT now() NOT NULL
);

-- Bảng orders (đơn hàng)
CREATE TABLE public.orders (
    id uuid DEFAULT gen_random_uuid() NOT NULL PRIMARY KEY,
    user_id uuid REFERENCES public.users(id) ON DELETE CASCADE NOT NULL,
    service_id uuid REFERENCES public.services(id) ON DELETE CASCADE NOT NULL,
    quantity integer NOT NULL CHECK (quantity > 0),
    unit_price numeric(10,2) NOT NULL CHECK (unit_price >= 0),
    total_amount numeric(15,2) NOT NULL CHECK (total_amount >= 0),
    status text DEFAULT 'pending' NOT NULL CHECK (status IN ('pending', 'processing', 'completed', 'cancelled', 'refunded')),
    notes text,
    created_at timestamp with time zone DEFAULT now() NOT NULL,
    updated_at timestamp with time zone DEFAULT now() NOT NULL
);

-- Bảng transactions (giao dịch)
CREATE TABLE public.transactions (
    id uuid DEFAULT gen_random_uuid() NOT NULL PRIMARY KEY,
    user_id uuid REFERENCES public.users(id) ON DELETE CASCADE NOT NULL,
    order_id uuid REFERENCES public.orders(id) ON DELETE SET NULL,
    amount numeric(15,2) NOT NULL,
    type text NOT NULL CHECK (type IN ('deposit', 'withdrawal', 'payment', 'refund', 'commission')),
    status text DEFAULT 'completed' NOT NULL CHECK (status IN ('pending', 'completed', 'failed', 'cancelled')),
    description text,
    reference_id text, -- Mã tham chiếu bên ngoài
    created_at timestamp with time zone DEFAULT now() NOT NULL
);

-- 2. SƠ ĐỒ TỔ CHỨC DATABASE VÀ HƯỚNG DẪN DEVELOPER
-- =============================================

/*
┌─────────────────────────────────────────────────────────────────────────────┐
│                        DATABASE ARCHITECTURE OVERVIEW                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  ┌─────────────┐    ┌─────────────┐    ┌─────────────┐    ┌─────────────┐   │
│  │ auth.users  │    │   users     │    │   wallets   │    │ services    │   │
│  │ (Supabase)  │───▶│  (profile)  │───▶│  (balance)  │    │ (products)  │   │
│  └─────────────┘    └─────────────┘    └─────────────┘    └─────────────┘   │
│                             │                                      │         │
│                             │                                      │         │
│                             ▼                                      ▼         │
│                      ┌─────────────┐                                        │
│                      │   orders    │◀──────────────────────────────────────┘ │
│                      │ (purchases) │                                         │
│                      └─────────────┘                                         │
│                             │                                                │
│                             │                                                │
│                             ▼                                                │
│                      ┌─────────────┐                                        │
│                      │transactions │                                        │
│                      │ (payments)  │                                        │
│                      └─────────────┘                                        │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘

QUAN HỆ GIỮA CÁC BẢNG:
==================
1. auth.users (Supabase) → users (1:1) - Thông tin profile mở rộng
2. users → wallets (1:1) - Mỗi user có 1 wallet
3. users → orders (1:n) - User có thể có nhiều đơn hàng
4. services → orders (1:n) - Service có thể được order nhiều lần
5. orders → transactions (1:n) - Mỗi order có thể có nhiều transaction
6. users → transactions (1:n) - User có thể có nhiều giao dịch

LUỒNG DỮ LIỆU CHÍNH:
===================
User Register → Auto Create Wallet → Browse Services → Create Order → Payment Transaction → Update Wallet Balance

HƯỚNG DẪN DEVELOPER:
===================
*/

-- A. BẢNG USERS - Thông tin người dùng
-- ====================================
-- Mục đích: Lưu profile mở rộng từ auth.users
-- Lưu ý: id phải match với auth.users.id, email phải unique
-- Trường quan trọng: is_admin (phân quyền), status (trạng thái tài khoản)

-- B. BẢNG SERVICES - Danh mục dịch vụ  
-- ===================================
-- Mục đích: Quản lý các dịch vụ/sản phẩm bán
-- Lưu ý: price phải >= 0, is_active để show/hide service
-- Trường quan trọng: name, price, is_active, category

-- C. BẢNG WALLETS - Ví tiền người dùng
-- ====================================
-- Mục đích: Lưu số dư của từng user
-- Lưu ý: Tự động tạo khi user đăng ký, balance >= 0
-- Trường quan trọng: user_id (unique), balance

-- D. BẢNG ORDERS - Đơn hàng
-- =========================
-- Mục đích: Lưu thông tin đơn hàng của user
-- Lưu ý: total_amount = unit_price * quantity
-- Workflow: pending → processing → completed/cancelled/refunded
-- Trường quan trọng: user_id, service_id, status, total_amount

-- E. BẢNG TRANSACTIONS - Giao dịch tài chính
-- ==========================================
-- Mục đích: Lưu lịch sử giao dịch (nạp tiền, thanh toán, hoàn tiền)
-- Lưu ý: amount có thể âm/dương, order_id có thể null (nạp tiền)
-- Types: deposit (+), withdrawal (-), payment (-), refund (+), commission
-- Trường quan trọng: user_id, amount, type, status

-- QUAN HỆ FOREIGN KEYS:
-- =====================
-- users.id → auth.users.id (CASCADE DELETE)
-- wallets.user_id → users.id (CASCADE DELETE, UNIQUE)
-- orders.user_id → users.id (CASCADE DELETE)
-- orders.service_id → services.id (CASCADE DELETE)
-- transactions.user_id → users.id (CASCADE DELETE)
-- transactions.order_id → orders.id (SET NULL) - Cho phép null

-- BUSINESS LOGIC QUAN TRỌNG:
-- ==========================
-- 1. Khi user mới tạo → Auto tạo wallet với balance = 0
-- 2. Khi transaction status = 'completed' → Auto cập nhật wallet balance
-- 3. Order chỉ có thể update khi status = 'pending'
-- 4. Wallet balance không được < 0 (CHECK constraint)
-- 5. Quantity và price phải > 0

-- CÁC TRẠNG THÁI QUAN TRỌNG:
-- ==========================
-- User Status: active, inactive, suspended
-- Order Status: pending, processing, completed, cancelled, refunded  
-- Transaction Status: pending, completed, failed, cancelled
-- Transaction Types: deposit, withdrawal, payment, refund, commission

-- INDEXES ĐỂ TỐI ƯU HIỆU SUẤT
-- ============================

-- Indexes cho bảng users (tìm kiếm theo email, admin, status)
CREATE INDEX idx_users_email ON public.users(email);
CREATE INDEX idx_users_is_admin ON public.users(is_admin);
CREATE INDEX idx_users_status ON public.users(status);
CREATE INDEX idx_users_created_at ON public.users(created_at);

-- Indexes cho bảng services (filter active, category)
CREATE INDEX idx_services_is_active ON public.services(is_active);
CREATE INDEX idx_services_category ON public.services(category);
CREATE INDEX idx_services_created_at ON public.services(created_at);

-- Indexes cho bảng orders (quan trọng nhất - query nhiều)
CREATE INDEX idx_orders_user_id ON public.orders(user_id);
CREATE INDEX idx_orders_service_id ON public.orders(service_id);
CREATE INDEX idx_orders_status ON public.orders(status);
CREATE INDEX idx_orders_created_at ON public.orders(created_at);
CREATE INDEX idx_orders_user_status ON public.orders(user_id, status); -- Composite index

-- Indexes cho bảng transactions (query theo user, order, type)
CREATE INDEX idx_transactions_user_id ON public.transactions(user_id);
CREATE INDEX idx_transactions_order_id ON public.transactions(order_id);
CREATE INDEX idx_transactions_type ON public.transactions(type);
CREATE INDEX idx_transactions_status ON public.transactions(status);
CREATE INDEX idx_transactions_created_at ON public.transactions(created_at);
CREATE INDEX idx_transactions_user_type ON public.transactions(user_id, type); -- Composite index

-- 3. TẠO CÁC FUNCTIONS VÀ TRIGGERS
-- =============================================

-- Function để cập nhật updated_at tự động
CREATE OR REPLACE FUNCTION public.update_updated_at_column()
RETURNS TRIGGER AS $$
BEGIN
    NEW.updated_at = now();
    RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Triggers cho updated_at
CREATE TRIGGER update_users_updated_at
    BEFORE UPDATE ON public.users
    FOR EACH ROW EXECUTE FUNCTION public.update_updated_at_column();

CREATE TRIGGER update_services_updated_at
    BEFORE UPDATE ON public.services
    FOR EACH ROW EXECUTE FUNCTION public.update_updated_at_column();

CREATE TRIGGER update_orders_updated_at
    BEFORE UPDATE ON public.orders
    FOR EACH ROW EXECUTE FUNCTION public.update_updated_at_column();

CREATE TRIGGER update_wallets_updated_at
    BEFORE UPDATE ON public.wallets
    FOR EACH ROW EXECUTE FUNCTION public.update_updated_at_column();

-- Function để tạo wallet tự động khi user mới được tạo
CREATE OR REPLACE FUNCTION public.handle_new_user()
RETURNS TRIGGER AS $$
BEGIN
    INSERT INTO public.wallets (user_id, balance)
    VALUES (NEW.id, 0.00);
    RETURN NEW;
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;

-- Trigger tạo wallet cho user mới
CREATE TRIGGER on_auth_user_created
    AFTER INSERT ON auth.users
    FOR EACH ROW EXECUTE FUNCTION public.handle_new_user();

-- Function để cập nhật balance wallet khi có transaction
CREATE OR REPLACE FUNCTION public.update_wallet_balance()
RETURNS TRIGGER AS $$
BEGIN
    IF TG_OP = 'INSERT' AND NEW.status = 'completed' THEN
        UPDATE public.wallets 
        SET balance = balance + NEW.amount 
        WHERE user_id = NEW.user_id;
    END IF;
    
    IF TG_OP = 'UPDATE' AND OLD.status != 'completed' AND NEW.status = 'completed' THEN
        UPDATE public.wallets 
        SET balance = balance + NEW.amount 
        WHERE user_id = NEW.user_id;
    END IF;
    
    IF TG_OP = 'UPDATE' AND OLD.status = 'completed' AND NEW.status != 'completed' THEN
        UPDATE public.wallets 
        SET balance = balance - OLD.amount 
        WHERE user_id = OLD.user_id;
    END IF;
    
    RETURN COALESCE(NEW, OLD);
END;
$$ LANGUAGE plpgsql SECURITY DEFINER;

-- Trigger cập nhật wallet balance
CREATE TRIGGER update_wallet_on_transaction
    AFTER INSERT OR UPDATE ON public.transactions
    FOR EACH ROW EXECUTE FUNCTION public.update_wallet_balance();

-- 4. KÍCH HOẠT ROW LEVEL SECURITY
-- =============================================

ALTER TABLE public.users ENABLE ROW LEVEL SECURITY;
ALTER TABLE public.services ENABLE ROW LEVEL SECURITY;
ALTER TABLE public.orders ENABLE ROW LEVEL SECURITY;
ALTER TABLE public.transactions ENABLE ROW LEVEL SECURITY;
ALTER TABLE public.wallets ENABLE ROW LEVEL SECURITY;

-- 5. TẠO CÁC RLS POLICIES
-- =============================================

-- ===== POLICIES CHO BẢNG USERS =====

-- Cho phép user xem profile của chính mình
CREATE POLICY "users_select_own" ON public.users
    FOR SELECT USING (auth.uid() = id);

-- Cho phép admin xem tất cả user profiles
CREATE POLICY "users_select_admin" ON public.users
    FOR SELECT USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- Cho phép user cập nhật profile của chính mình
CREATE POLICY "users_update_own" ON public.users
    FOR UPDATE USING (auth.uid() = id)
    WITH CHECK (auth.uid() = id);

-- Cho phép admin cập nhật bất kỳ user nào
CREATE POLICY "users_update_admin" ON public.users
    FOR UPDATE USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- Cho phép admin tạo user mới
CREATE POLICY "users_insert_admin" ON public.users
    FOR INSERT WITH CHECK (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- Cho phép admin xóa user
CREATE POLICY "users_delete_admin" ON public.users
    FOR DELETE USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- ===== POLICIES CHO BẢNG SERVICES =====

-- Cho phép tất cả user đã xác thực xem services
CREATE POLICY "services_select_all" ON public.services
    FOR SELECT USING (auth.role() = 'authenticated');

-- Cho phép admin quản lý services
CREATE POLICY "services_manage_admin" ON public.services
    FOR ALL USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- ===== POLICIES CHO BẢNG ORDERS =====

-- Cho phép user xem orders của chính mình
CREATE POLICY "orders_select_own" ON public.orders
    FOR SELECT USING (auth.uid() = user_id);

-- Cho phép user tạo order cho chính mình
CREATE POLICY "orders_insert_own" ON public.orders
    FOR INSERT WITH CHECK (auth.uid() = user_id);

-- Cho phép user cập nhật order của chính mình (giới hạn)
CREATE POLICY "orders_update_own" ON public.orders
    FOR UPDATE USING (auth.uid() = user_id AND status = 'pending')
    WITH CHECK (auth.uid() = user_id);

-- Cho phép admin quản lý tất cả orders
CREATE POLICY "orders_manage_admin" ON public.orders
    FOR ALL USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- ===== POLICIES CHO BẢNG TRANSACTIONS =====

-- Cho phép user xem transactions của chính mình
CREATE POLICY "transactions_select_own" ON public.transactions
    FOR SELECT USING (auth.uid() = user_id);

-- Cho phép user tạo transaction cho chính mình
CREATE POLICY "transactions_insert_own" ON public.transactions
    FOR INSERT WITH CHECK (auth.uid() = user_id);

-- Cho phép admin quản lý tất cả transactions
CREATE POLICY "transactions_manage_admin" ON public.transactions
    FOR ALL USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- ===== POLICIES CHO BẢNG WALLETS =====

-- Cho phép user xem wallet của chính mình
CREATE POLICY "wallets_select_own" ON public.wallets
    FOR SELECT USING (auth.uid() = user_id);

-- Cho phép user cập nhật wallet của chính mình (thông qua transactions)
CREATE POLICY "wallets_update_own" ON public.wallets
    FOR UPDATE USING (auth.uid() = user_id)
    WITH CHECK (auth.uid() = user_id);

-- Cho phép admin quản lý tất cả wallets
CREATE POLICY "wallets_manage_admin" ON public.wallets
    FOR ALL USING (
        EXISTS (
            SELECT 1 FROM public.users 
            WHERE id = auth.uid() AND is_admin = true
        )
    );

-- 6. TẠO CÁC VIEWS HỖ TRỢ
-- =============================================

-- View để hiển thị thông tin order với service name
CREATE VIEW public.order_details AS
SELECT 
    o.*,
    s.name as service_name,
    s.category as service_category,
    u.full_name as user_name,
    u.email as user_email
FROM public.orders o
JOIN public.services s ON o.service_id = s.id
JOIN public.users u ON o.user_id = u.id;

-- View để hiển thị thống kê dashboard
CREATE VIEW public.dashboard_stats AS
SELECT 
    (SELECT COUNT(*) FROM public.users WHERE created_at >= CURRENT_DATE - INTERVAL '30 days') as new_users_30d,
    (SELECT COUNT(*) FROM public.orders WHERE created_at >= CURRENT_DATE - INTERVAL '30 days') as new_orders_30d,
    (SELECT SUM(total_amount) FROM public.orders WHERE status = 'completed' AND created_at >= CURRENT_DATE - INTERVAL '30 days') as revenue_30d,
    (SELECT COUNT(*) FROM public.services WHERE is_active = true) as active_services,
    (SELECT COUNT(*) FROM public.orders WHERE status = 'pending') as pending_orders;

-- 7. HƯỚNG DẪN NHẬP LIỆU VÀ SAMPLE DATA
-- =============================================

/*
HƯỚNG DẪN NHẬP LIỆU THEO THỨ TỰ:
===============================
1. Tạo users trước (sau khi auth.users đã có)
2. Wallets sẽ tự động tạo qua trigger
3. Tạo services 
4. Tạo orders
5. Tạo transactions (sẽ tự động update wallet balance)

LƯU Ý QUAN TRỌNG KHI NHẬP LIỆU:
==============================
- users.id phải match với auth.users.id
- orders.total_amount = unit_price * quantity
- transactions.amount: + cho nhận tiền, - cho trả tiền
- Wallet balance sẽ tự động cập nhật khi transaction completed
*/

-- SAMPLE DATA NHẬP LIỆU TUẦN TỰ
-- ==============================

-- 1. NHẬP USERS (sau khi đã có auth.users)
INSERT INTO public.users (id, email, full_name, is_admin, status, created_at) VALUES
-- Admin user  
('a0eebc99-9c0b-4ef8-bb6d-6bb9bd380a11', 'admin@servicehub.com', 'System Administrator', true, 'active', '2024-01-01 10:00:00+00'),
-- Regular users
('b0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12', 'john.doe@gmail.com', 'John Doe', false, 'active', '2024-01-05 11:30:00+00'),
('c0eebc99-9c0b-4ef8-bb6d-6bb9bd380a13', 'jane.smith@gmail.com', 'Jane Smith', false, 'active', '2024-01-10 14:00:00+00'),
('d0eebc99-9c0b-4ef8-bb6d-6bb9bd380a14', 'mike.wilson@gmail.com', 'Mike Wilson', false, 'inactive', '2024-01-15 09:00:00+00');

-- 2. NHẬP SERVICES 
INSERT INTO public.services (id, name, description, price, is_active, category, created_at) VALUES
('s1000000-0000-0000-0000-000000000001', 'Social Media Boost', 'Increase your social media followers and engagement', 9.99, true, 'social-media', '2024-01-02 09:00:00+00'),
('s1000000-0000-0000-0000-000000000002', 'Website Traffic Package', 'Drive targeted traffic to your website', 29.99, true, 'traffic', '2024-01-03 10:00:00+00'),
('s1000000-0000-0000-0000-000000000003', 'SEO Optimization', 'Improve your website search engine ranking', 79.99, true, 'seo', '2024-01-04 11:00:00+00'),
('s1000000-0000-0000-0000-000000000004', 'Content Writing', 'Professional content writing services', 49.99, true, 'content', '2024-01-06 13:00:00+00'),
('s1000000-0000-0000-0000-000000000005', 'Logo Design', 'Custom logo design for your brand', 99.99, false, 'design', '2024-01-07 14:00:00+00');

-- 3. NHẬP ORDERS
INSERT INTO public.orders (id, user_id, service_id, quantity, unit_price, total_amount, status, created_at) VALUES
-- John's orders
('o1000000-0000-0000-0000-000000000001', 'b0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12', 's1000000-0000-0000-0000-000000000001', 2, 9.99, 19.98, 'completed', '2024-01-07 10:00:00+00'),
('o1000000-0000-0000-0000-000000000002', 'b0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12', 's1000000-0000-0000-0000-000000000002', 1, 29.99, 29.99, 'processing', '2024-01-08 14:00:00+00'),
-- Jane's orders  
('o1000000-0000-0000-0000-000000000003', 'c0eebc99-9c0b-4ef8-bb6d-6bb9bd380a13', 's1000000-0000-0000-0000-000000000003', 1, 79.99, 79.99, 'completed', '2024-01-12 09:00:00+00'),
('o1000000-0000-0000-0000-000000000004', 'c0eebc99-9c0b-4ef8-bb6d-6bb9bd380a13', 's1000000-0000-0000-0000-000000000004', 2, 49.99, 99.98, 'cancelled', '2024-01-15 11:00:00+00'),
-- Mike's orders
('o1000000-0000-0000-0000-000000000005', 'd0eebc99-9c0b-4ef8-bb6d-6bb9bd380a14', 's1000000-0000-0000-0000-000000000001', 1, 9.99, 9.99, 'pending', '2024-01-18 16:00:00+00');

-- 4. NHẬP TRANSACTIONS (sẽ tự động update wallet balance)
INSERT INTO public.transactions (id, user_id, order_id, amount, type, status, description, created_at) VALUES
-- John's transactions
('t1000000-0000-0000-0000-000000000001', 'b0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12', NULL, 100.00, 'deposit', 'completed', 'Wallet top-up via PayPal', '2024-01-06 10:00:00+00'),
('t1000000-0000-0000-0000-000000000002', 'b0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12', 'o1000000-0000-0000-0000-000000000001', -19.98, 'payment', 'completed', 'Payment for Social Media Boost x2', '2024-01-07 10:01:00+00'),
('t1000000-0000-0000-0000-000000000003', 'b0eebc99-9c0b-4ef8-bb6d-6bb9bd380a12', 'o1000000-0000-0000-0000-000000000002', -29.99, 'payment', 'completed', 'Payment for Website Traffic Package', '2024-01-08 14:01:00+00'),

-- Jane's transactions
('t1000000-0000-0000-0000-000000000004', 'c0eebc99-9c0b-4ef8-bb6d-6bb9bd380a13', NULL, 200.00, 'deposit', 'completed', 'Wallet top-up via Credit Card', '2024-01-11 11:00:00+00'),
('t1000000-0000-0000-0000-000000000005', 'c0eebc99-9c0b-4ef8-bb6d-6bb9bd380a13', 'o1000000-0000-0000-0000-000000000003', -79.99, 'payment', 'completed', 'Payment for SEO Optimization', '2024-01-12 09:01:00+00'),
('t1000000-0000-0000-0000-000000000006', 'c0eebc99-9c0b-4ef8-bb6d-6bb9bd380a13', 'o1000000-0000-0000-0000-000000000004', 99.98, 'refund', 'completed', 'Refund for cancelled Content Writing order', '2024-01-15 11:15:00+00'),

-- Mike's transactions
('t1000000-0000-0000-0000-000000000007', 'd0eebc99-9c0b-4ef8-bb6d-6bb9bd380a14', NULL, 50.00, 'deposit', 'completed', 'Wallet top-up via Bank Transfer', '2024-01-17 15:00:00+00');

-- 5. KIỂM TRA KẾT QUẢ WALLET BALANCE (sau khi nhập transactions)
/*
Expected wallet balances:
- John (b0eebc99...): 100.00 - 19.98 - 29.99 = 50.03
- Jane (c0eebc99...): 200.00 - 79.99 + 99.98 = 219.99  
- Mike (d0eebc99...): 50.00 = 50.00
*/

-- QUERY KIỂM TRA DỮ LIỆU
-- ======================

-- Kiểm tra wallet balance
SELECT 
    u.full_name,
    u.email,
    w.balance,
    (SELECT COUNT(*) FROM orders WHERE user_id = u.id) as total_orders,
    (SELECT COUNT(*) FROM transactions WHERE user_id = u.id) as total_transactions
FROM users u
JOIN wallets w ON u.id = w.user_id
ORDER BY u.created_at;

-- Kiểm tra order details
SELECT 
    o.id,
    u.full_name as customer,
    s.name as service,
    o.quantity,
    o.total_amount,
    o.status,
    o.created_at
FROM orders o
JOIN users u ON o.user_id = u.id
JOIN services s ON o.service_id = s.id
ORDER BY o.created_at;

-- Kiểm tra transaction history
SELECT 
    t.id,
    u.full_name as user,
    t.amount,
    t.type,
    t.status,
    t.description,
    t.created_at
FROM transactions t
JOIN users u ON t.user_id = u.id
ORDER BY t.created_at;

-- 8. COMMENT VÀ DOCUMENTATION
-- =============================================

COMMENT ON TABLE public.users IS 'Bảng người dùng mở rộng từ auth.users - chứa profile và phân quyền';
COMMENT ON TABLE public.services IS 'Bảng quản lý các dịch vụ/sản phẩm có thể bán';
COMMENT ON TABLE public.orders IS 'Bảng đơn hàng - tracking mua bán giữa user và service';
COMMENT ON TABLE public.transactions IS 'Bảng giao dịch tài chính - log mọi thay đổi tiền';
COMMENT ON TABLE public.wallets IS 'Bảng ví tiền của người dùng - số dư hiện tại';

COMMENT ON COLUMN public.users.is_admin IS 'Xác định user có phải admin không - dùng cho phân quyền RLS';
COMMENT ON COLUMN public.users.status IS 'Trạng thái tài khoản: active, inactive, suspended';
COMMENT ON COLUMN public.services.is_active IS 'Service có đang bán không - false = tạm ngưng';
COMMENT ON COLUMN public.orders.status IS 'Workflow: pending → processing → completed/cancelled/refunded';
COMMENT ON COLUMN public.orders.total_amount IS 'Tự tính = unit_price * quantity';
COMMENT ON COLUMN public.transactions.type IS 'deposit(+), withdrawal(-), payment(-), refund(+), commission(+)';
COMMENT ON COLUMN public.transactions.amount IS 'Số tiền: dương = nhận, âm = trả';
COMMENT ON COLUMN public.transactions.status IS 'pending, completed, failed, cancelled';
COMMENT ON COLUMN public.wallets.balance IS 'Số dư hiện tại - tự động cập nhật qua transaction triggers';

-- 9. THIẾT LẬP PERMISSIONS
-- =============================================

-- Grant permissions cho authenticated users
GRANT USAGE ON SCHEMA public TO authenticated;
GRANT ALL ON ALL TABLES IN SCHEMA public TO authenticated;
GRANT ALL ON ALL SEQUENCES IN SCHEMA public TO authenticated;
GRANT ALL ON ALL FUNCTIONS IN SCHEMA public TO authenticated;

-- Grant permissions cho anon users (nếu cần)
GRANT USAGE ON SCHEMA public TO anon;
GRANT SELECT ON public.services TO anon; -- Cho phép xem services mà không cần login

-- 10. HELPER FUNCTIONS CHO DEVELOPERS
-- ===================================

-- Function kiểm tra user có phải admin không
CREATE OR REPLACE FUNCTION public.is_admin(user_id uuid DEFAULT auth.uid())
RETURNS boolean AS $
BEGIN
    RETURN EXISTS (
        SELECT 1 FROM public.users 
        WHERE id = user_id AND is_admin = true
    );
END;
$ LANGUAGE plpgsql SECURITY DEFINER;

-- Function lấy wallet balance của user
CREATE OR REPLACE FUNCTION public.get_wallet_balance(user_id uuid DEFAULT auth.uid())
RETURNS numeric AS $
BEGIN
    RETURN (
        SELECT balance 
        FROM public.wallets 
        WHERE user_id = $1
    );
END;
$ LANGUAGE plpgsql SECURITY DEFINER;

-- Function kiểm tra user có đủ tiền trong ví không
CREATE OR REPLACE FUNCTION public.has_sufficient_balance(user_id uuid, required_amount numeric)
RETURNS boolean AS $
BEGIN
    RETURN (
        SELECT balance >= required_amount
        FROM public.wallets 
        WHERE user_id = $1
    );
END;
$ LANGUAGE plpgsql SECURITY DEFINER;

-- 11. VALIDATION TRIGGERS (BỔ SUNG)
-- =================================

-- Trigger kiểm tra user có đủ tiền khi tạo payment transaction
CREATE OR REPLACE FUNCTION public.validate_payment_transaction()
RETURNS TRIGGER AS $
BEGIN
    -- Chỉ check cho payment transactions
    IF NEW.type = 'payment' AND NEW.amount < 0 AND NEW.status = 'completed' THEN
        -- Kiểm tra balance trước khi trừ tiền
        IF NOT public.has_sufficient_balance(NEW.user_id, ABS(NEW.amount)) THEN
            RAISE EXCEPTION 'Insufficient wallet balance for payment';
        END IF;
    END IF;
    
    RETURN NEW;
END;
$ LANGUAGE plpgsql;

CREATE TRIGGER validate_payment_before_insert
    BEFORE INSERT ON public.transactions
    FOR EACH ROW EXECUTE FUNCTION public.validate_payment_transaction();

-- 12. USEFUL QUERIES CHO DEVELOPERS
-- =================================

/*
-- Lấy tất cả orders của user với service details
SELECT 
    o.*,
    s.name as service_name,
    s.price as service_price
FROM orders o
JOIN services s ON o.service_id = s.id
WHERE o.user_id = auth.uid()
ORDER BY o.created_at DESC;

-- Lấy transaction history của user
SELECT 
    t.*,
    o.id as order_reference
FROM transactions t
LEFT JOIN orders o ON t.order_id = o.id
WHERE t.user_id = auth.uid()
ORDER BY t.created_at DESC;

-- Lấy dashboard stats (chỉ admin)
SELECT 
    (SELECT COUNT(*) FROM users WHERE created_at >= CURRENT_DATE - INTERVAL '30 days') as new_users_30d,
    (SELECT COUNT(*) FROM orders WHERE created_at >= CURRENT_DATE - INTERVAL '30 days') as new_orders_30d,
    (SELECT COALESCE(SUM(total_amount), 0) FROM orders WHERE status = 'completed' AND created_at >= CURRENT_DATE - INTERVAL '30 days') as revenue_30d,
    (SELECT COUNT(*) FROM services WHERE is_active = true) as active_services,
    (SELECT COUNT(*) FROM orders WHERE status = 'pending') as pending_orders;

-- Kiểm tra wallet balance consistency
SELECT 
    u.email,
    w.balance as wallet_balance,
    COALESCE(SUM(t.amount), 0) as calculated_balance
FROM users u
JOIN wallets w ON u.id = w.user_id
LEFT JOIN transactions t ON u.id = t.user_id AND t.status = 'completed'
GROUP BY u.id, u.email, w.balance
HAVING w.balance != COALESCE(SUM(t.amount), 0);
*/
---

