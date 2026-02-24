# 🌍 Tourvisto – A Travel Dashboard

[![Deployed on Vercel](https://img.shields.io/badge/Deployed%20on-Vercel-black?style=for-the-badge&logo=vercel)](https://tourvisto-nine.vercel.app/)

A full-stack travel agency dashboard built with **React**, **React Router v7**, **Appwrite**, and **Gemini AI**. Admins can generate AI-powered travel itineraries, manage users, and track activity — while users can browse and book trips.

🔗 **Live Demo**: [tourvisto-nine.vercel.app](https://tourvisto-nine.vercel.app)

---

## 📸 Screenshots

### Sign In
![Sign In](screenshots/Screenshot%20(2579).png)

### Home Page
![Home Page](screenshots/Screenshot%20(2580).png)

### Featured Travel Destinations
![Travel Destinations](screenshots/Screenshot%20(2581).png)

### Admin Dashboard
![Admin Dashboard](screenshots/Screenshot%20(2582).png)

### Manage Users
![Users](screenshots/Screenshot%20(2583).png)

### Generate Trip – Form
![Generate Trip Form](screenshots/Screenshot%20(2584).png)

### Generate Trip – World Map
![Generate Trip Map](screenshots/Screenshot%20(2585).png)

---

## 📸 Screenshots

### Sign In
![Sign In](screenshots/Screenshot%20(2579).png)

### Home Page
![Home Page](screenshots/Screenshot%20(2580).png)

### Featured Travel Destinations
![Featured Destinations](screenshots/Screenshot%20(2581).png)

### Admin Dashboard
![Admin Dashboard](screenshots/Screenshot%20(2582).png)

### Manage Users
![Manage Users](screenshots/Screenshot%20(2583).png)

### Generate Trip – Form
![Generate Trip Form](screenshots/Screenshot%20(2584).png)

### Generate Trip – World Map
![Generate Trip Map](screenshots/Screenshot%20(2585).png)

---

## ✨ Features

### 👤 For Users
- Sign in with Google (OAuth)
- Browse featured travel destinations
- View handpicked AI-generated trips
- View full trip detail pages with itinerary, weather info, and best time to visit
- Book trips via Stripe payment links

### 🔐 For Admins
- Full dashboard with real-time stats (total users, trips, active users)
- Syncfusion charts — travel styles, trips by interest
- Manage all users
- View and manage all AI-generated trips
- Generate new trips using Gemini AI

### 🤖 AI & Integrations
- **Gemini AI** — generates full day-by-day itineraries, weather info, activities, and pricing
- **Unsplash** — automatically fetches beautiful destination photos
- **Stripe** — creates payment links for each generated trip
- **Appwrite** — handles authentication, database, and storage

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React 19, React Router v7 |
| UI Components | Syncfusion (charts, grids, maps) |
| Backend/Auth | Appwrite Cloud |
| AI | Google Gemini 1.5 Flash |
| Images | Unsplash API |
| Payments | Stripe |
| Deployment | Vercel |
| Styling | Tailwind CSS |
| Monitoring | Sentry |

---

## 🚀 Getting Started

### Prerequisites
- Node.js 18+
- Accounts on: [Appwrite Cloud](https://cloud.appwrite.io), [Google AI Studio](https://aistudio.google.com), [Unsplash Developers](https://unsplash.com/developers), [Stripe](https://stripe.com)

### 1. Clone the repo
```bash
git clone https://github.com/nimishaaaaaw/tourvisto.git
cd tourvisto
npm install
```

### 2. Set up environment variables
Create a `.env.local` file in the root:

```env
VITE_APPWRITE_PROJECT_ID=your_project_id
VITE_APPWRITE_API_ENDPOINT=https://cloud.appwrite.io/v1
VITE_APPWRITE_API_KEY=your_api_key
VITE_APPWRITE_DATABASE_ID=your_database_id
VITE_APPWRITE_TRIPS_COLLECTION_ID=your_trips_collection_id
VITE_APPWRITE_USERS_COLLECTION_ID=your_users_collection_id
GEMINI_API_KEY=your_gemini_api_key
UNSPLASH_ACCESS_KEY=your_unsplash_key
STRIPE_SECRET_KEY=sk_test_...
VITE_BASE_URL=http://localhost:5173
VITE_SYNCFUSION_LICENSE_KEY=your_syncfusion_key (optional)
```

### 3. Set up Appwrite

**Create a Database** with two collections:

**`users` collection attributes:**
- `accountId` — String, required
- `name` — String
- `email` — String
- `imageUrl` — String
- `joinedAt` — String
- `status` — String (values: `user` or `admin`)
- `role` — String

**`itinerary` collection attributes:**
- `userId` — String, required
- `tripDetails` — String (stores JSON)
- `imageUrls` — String[]
- `createdAt` — String
- `payment_link` — String

Set permissions on both collections: **Any → Read, Create, Update**

### 4. Enable Google OAuth in Appwrite
- Appwrite → Auth → Settings → Enable Google
- Add your Google OAuth Client ID and Secret
- Add authorized redirect URI:
```
https://cloud.appwrite.io/v1/account/sessions/oauth2/callback/google/YOUR_PROJECT_ID
```

### 5. Run locally
```bash
npm run dev
```

Open [http://localhost:5173](http://localhost:5173)

---

## 🌐 Deployment (Vercel)

1. Push your code to GitHub
2. Import the repo on [vercel.com](https://vercel.com)
3. Add all environment variables from `.env.local` to Vercel's environment settings
4. Update `VITE_BASE_URL` to your Vercel URL
5. Add your Vercel domain to Appwrite's Web Platforms
6. Add your Vercel domain to Google OAuth's authorized origins

---

## 📁 Project Structure

```
app/
├── appwrite/          # Appwrite client, auth, trips logic
├── components/        # Reusable UI components
├── constants/         # App constants and world map data
├── lib/               # Utility functions, Stripe integration
├── routes/
│   ├── admin/         # Admin dashboard, users, trips, create-trip
│   ├── api/           # API routes (create-trip with Gemini)
│   └── root/          # Public pages (travel page, trip detail)
public/
└── assets/            # Icons, images
```

---

## 🔑 Making a User an Admin

1. Go to Appwrite → your database → `users` collection
2. Find your user row
3. Set the `status` field to `admin`
4. Refresh the app — you'll see the Admin Panel link

---

## 📝 Environment Variables Reference

| Variable | Description |
|----------|-------------|
| `VITE_APPWRITE_PROJECT_ID` | Your Appwrite project ID |
| `VITE_APPWRITE_API_ENDPOINT` | `https://cloud.appwrite.io/v1` |
| `VITE_APPWRITE_API_KEY` | Appwrite API key (all scopes) |
| `VITE_APPWRITE_DATABASE_ID` | Your Appwrite database ID |
| `VITE_APPWRITE_TRIPS_COLLECTION_ID` | Trips collection ID |
| `VITE_APPWRITE_USERS_COLLECTION_ID` | Users collection ID |
| `GEMINI_API_KEY` | Google Gemini API key |
| `UNSPLASH_ACCESS_KEY` | Unsplash API access key |
| `STRIPE_SECRET_KEY` | Stripe secret key (`sk_test_...`) |
| `VITE_BASE_URL` | App base URL (localhost or Vercel) |

---

## 🙏 Credits

Original project concept by [Adrian Hajdin - JS Mastery]
Built and deployed by [@nimishaaaaaw](https://github.com/nimishaaaaaw).
