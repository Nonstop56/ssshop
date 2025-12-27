# Soft Stop Shop 🛒 www.softstopshop.com
ระบบ E-Commerce แบบครบวงจร สำหรับขายสินค้าทั้งแบบ Physical และ Digital พร้อมระบบ License Key

## ✨ Features

### 🛍️ ร้านค้า
- สินค้า Physical (จัดส่ง) และ Digital (ดาวน์โหลด)
- ระบบตะกร้าสินค้า (Cart)
- ระบบค้นหาและกรองสินค้า
- หมวดหมู่สินค้า

### 🔐 ระบบ License
- สร้าง License Key อัตโนมัติเมื่อซื้อสินค้าดิจิทัล
- API ตรวจสอบ License
- จำกัดจำนวนการ Activate
- ระบบหมดอายุ

### 💳 การชำระเงิน
- Stripe (Credit/Debit Card)
- PromptPay (QR Code)
- Webhook รับแจ้งเตือนอัตโนมัติ

### 👤 ระบบผู้ใช้
- สมัครสมาชิก / เข้าสู่ระบบ
- OAuth (Google, GitHub)
- Dashboard ผู้ใช้
- ประวัติการสั่งซื้อ
- จัดการ License

### 🔧 Admin Panel
- Dashboard สถิติยอดขาย
- จัดการสินค้า
- จัดการคำสั่งซื้อ
- จัดการ License
- จัดการลูกค้า

### 🎨 UI/UX
- Cyberpunk Neon Theme (น้ำเงิน-ม่วง-ดำ)
- Responsive Design
- Animation & Effects
- Dark Mode

## 🚀 Getting Started

### Prerequisites

- Node.js 18+
- PostgreSQL
- Stripe Account
- (Optional) Google OAuth, GitHub OAuth

### Installation

1. Clone และติดตั้ง dependencies:

```bash
git clone <repository-url>
cd soft-stop-shop
npm install
```

2. สร้างไฟล์ `.env`:

```bash
cp .env.example .env
```

3. แก้ไขค่าใน `.env`:

```env
DATABASE_URL="postgresql://..."
NEXTAUTH_SECRET="your-secret"
STRIPE_SECRET_KEY="sk_test_..."
```

4. สร้าง Database:

```bash
npm run db:push
npm run db:generate
```

5. รันโปรเจกต์:

```bash
npm run dev
```

เปิดเบราว์เซอร์ไปที่ [http://localhost:3000](http://localhost:3000)

## 📁 Project Structure

```
src/
├── app/                  # App Router pages
│   ├── admin/           # Admin panel pages
│   ├── api/             # API routes
│   ├── auth/            # Auth pages (login, register)
│   ├── cart/            # Cart page
│   ├── checkout/        # Checkout pages
│   ├── dashboard/       # User dashboard
│   └── shop/            # Shop pages
├── components/
│   ├── layout/          # Header, Footer
│   └── ui/              # UI components
├── lib/
│   ├── auth.ts          # NextAuth config
│   ├── db.ts            # Prisma client
│   └── utils.ts         # Utility functions
├── stores/              # Zustand stores
└── types/               # TypeScript types
```

## 🔌 API Endpoints

### Products
- `GET /api/products` - รายการสินค้า
- `POST /api/products` - สร้างสินค้า (Admin)
- `GET /api/products/[id]` - รายละเอียดสินค้า

### Cart
- `GET /api/cart` - ดูตะกร้า
- `POST /api/cart` - เพิ่มสินค้า

### Orders
- `GET /api/orders` - รายการคำสั่งซื้อ
- `POST /api/orders` - สร้างคำสั่งซื้อ

### Licenses
- `GET /api/licenses` - รายการ License
- `POST /api/licenses/validate` - ตรวจสอบ License

### Payment
- `POST /api/payment/create-session` - สร้าง Stripe session
- `POST /api/payment/webhook` - Stripe webhook

## 🛡️ License Validation API

```bash
POST /api/licenses/validate
Content-Type: application/json

{
  "licenseKey": "SSS-PREM-XXXX-YYYY-ZZZZ",
  "deviceId": "device-unique-id",
  "deviceName": "My Computer"
}
```

Response:
```json
{
  "valid": true,
  "product": "Premium Software License",
  "expiresAt": "2025-01-15T00:00:00.000Z",
  "activations": {
    "current": 2,
    "max": 3
  }
}
```

## 🎯 Tech Stack

- **Framework**: Next.js 14 (App Router)
- **Language**: TypeScript
- **Styling**: Tailwind CSS
- **Database**: PostgreSQL + Prisma ORM
- **Auth**: NextAuth.js
- **State**: Zustand
- **Payment**: Stripe
- **UI**: Custom components (ShadCN-style)

## 📝 License

MIT License

---

Made with 💜 by Soft Stop Shop Team
