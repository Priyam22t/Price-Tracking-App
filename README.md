# PricePulse 🚀  
**Smart Product Price Tracking & Automated Alerts**

PricePulse is a modern, full-stack web application that helps users track product prices across multiple e-commerce websites and get notified automatically when prices drop. It eliminates the need to manually revisit product pages by continuously monitoring prices in the background and visualizing trends over time.

---

## 🌟 What is PricePulse?

PricePulse allows users to paste any supported e-commerce product URL and instantly start tracking its price. The app scrapes product details, stores historical price data, runs automated daily checks, and sends email alerts when a price drop is detected.

It is built to be **secure**, **scalable**, and **production-ready**, using modern web technologies and best practices.

---

## ✨ Key Features

### 🔍 Product Price Tracking  
- Track products from multiple e-commerce platforms  
- Automatically extracts product name, price, currency, and image  
- Supports dynamic, JavaScript-heavy websites  

### 📊 Interactive Price History  
- Visualize price changes over time  
- Clean, responsive charts using real historical data  
- Helps users identify trends and best buying times  

### 🔔 Smart Email Alerts  
- Users receive email notifications when prices drop  
- Prevents spam by alerting only on meaningful price changes  

### 🔐 Secure Authentication  
- Google OAuth sign-in  
- Each user can only access their own tracked products  
- Fully enforced Row Level Security (RLS)  

### 🔄 Automated Daily Monitoring  
- Background cron jobs re-check all tracked products daily  
- Prices are updated automatically without user interaction  

### 🧠 AI-Powered Scraping  
- Uses Firecrawl to handle:
  - JavaScript rendering
  - Anti-bot protection
  - Rotating proxies
  - Structured AI-based data extraction  

---

## 🧰 Tech Stack

### Frontend
- **Next.js (App Router)** – Server actions & modern routing  
- **Tailwind CSS** – Utility-first responsive styling  
- **shadcn/ui** – Reusable and accessible UI components  
- **Recharts** – Interactive price history charts  

### Backend & Services
- **Supabase**
  - PostgreSQL database
  - Google Authentication
  - Row Level Security (RLS)
  - `pg_cron` for scheduled background jobs  
- **Firecrawl**
  - Web scraping with JavaScript rendering
  - AI-based structured extraction
  - Anti-bot & proxy handling  
- **Resend**
  - Transactional email delivery for alerts  

---

## 🔍 How PricePulse Works

### User Flow
1. User signs in using Google  
2. User pastes a product URL on the homepage  
3. Firecrawl extracts product details instantly  
4. Product is saved securely in Supabase  
5. User sees current price and price history chart  

### Automated Price Checks
- A scheduled cron job runs daily
- Triggers a secure API endpoint
- Re-scrapes all tracked products
- Saves new price history entries
- Sends email alerts if prices drop

---

## 📁 Project Structure

pricepulse/
├── app/
│ ├── page.js # Landing page
│ ├── actions.js # Server actions
│ ├── auth/callback/route.js # Google OAuth callback
│ └── api/cron/check-prices/route.js # Cron endpoint
├── components/
│ ├── ui/ # shadcn/ui components
│ ├── AddProductForm.js
│ ├── ProductCard.js
│ ├── PriceChart.js
│ └── AuthModal.js
├── lib/
│ ├── firecrawl.js # Firecrawl integration
│ ├── email.js # Email templates
│ └── utils.js
├── utils/supabase/
│ ├── client.js
│ ├── server.js
│ └── middleware.js
├── supabase/migrations/
│ ├── 001_schema.sql # DB schema & RLS
│ └── 002_setup_cron.sql # Cron job setup
└── .env.local

yaml
Copy code

---

## 🧪 Prerequisites

- Node.js **18+**
- Supabase account
- Firecrawl API key
- Resend API key
- Google OAuth credentials

---

## 🚀 Local Setup

### Clone & Install
```bash
git clone https://github.com/your-username/pricepulse.git
cd pricepulse
npm install
Environment Variables (.env.local)
env
Copy code
NEXT_PUBLIC_SUPABASE_URL=your_supabase_url
NEXT_PUBLIC_SUPABASE_ANON_KEY=your_anon_key
SUPABASE_SERVICE_ROLE_KEY=your_service_role_key

FIRECRAWL_API_KEY=your_firecrawl_api_key

RESEND_API_KEY=your_resend_api_key
RESEND_FROM_EMAIL=onboarding@resend.dev

CRON_SECRET=your_generated_secret
NEXT_PUBLIC_APP_URL=http://localhost:3000
Run the App
bash
Copy code
npm run dev
Open http://localhost:3000

☁️ Deployment
Deploy easily on Vercel

Add environment variables in Vercel dashboard

Update Supabase cron endpoint to production URL

App is production-ready and scalable

🐛 Common Issues & Tips
No price history shown
Price history appears after at least one automated price check runs.

Cron job not updating prices
Ensure SUPABASE_SERVICE_ROLE_KEY and CRON_SECRET are set correctly.

Scraping failures
Some websites block scraping; adjusting Firecrawl prompts can help.

Emails not delivered
Verify Resend API key and sender email setup.

🎨 Customization Ideas
Change cron frequency (hourly, daily, weekly)

Extract additional product data (brand, rating, availability)

Add price comparison features

Support multiple notification channels

🤝 Contributing
Contributions are welcome!

Fork the repository

Create a feature branch

Commit your changes

Open a pull request

📄 License
MIT License
