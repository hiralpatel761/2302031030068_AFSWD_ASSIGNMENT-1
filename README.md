# EduStream Prototype (React + Tailwind + Vite)

A functional prototype that covers **4+ key feature areas** from the case study:

- **Media Gallery & Playback**: HTML5 video/audio with Canvas overlay and media event handlers.
- **User Preferences & Dark Mode**: Theme toggle persisted across sessions.
- **Authentication & Purchases**: Simulated JWT auth, reusable cart, mocked checkout that you can swap for Laravel API.
- **Real-Time Validation**: Forms using HTML5 Constraint Validation API for instant feedback.
- **Dashboard & Analytics**: Recharts-based progress and time-spent charts.
- **Backend Integration Layer**: `src/mock/api.js` shows the interface you can implement in **Laravel + MongoDB**. Replace calls with your endpoints; keep the same function signatures.

## Quick Start

```bash
# 1) Extract this zip, then in the folder:
npm install

# 2) Start dev server
npm run dev

# 3) Open the local URL printed by Vite
```

> Note: The media gallery references public demo media URLs. Replace with your CDN URLs later.

## Where to Plug in Laravel + MongoDB

- Replace `src/mock/api.js` with real fetch calls (e.g., `/api/login`, `/api/courses`, `/api/orders`).
- Use **Laravel Sanctum or JWT** for auth tokens.
- MongoDB models: `users`, `courses`, `orders` collections.
- For background jobs (emails, processing uploads), dispatch **Laravel Queues** from your controllers; the frontend already calls `api.purchase()` which you can make enqueue a confirmation email job.

## File Map

- `src/context/AuthContext.jsx` – Auth state, token/user in localStorage.
- `src/context/CartContext.jsx` – Cart state with add/inc/dec/remove/total.
- `src/components/MediaGallery.jsx` – HTML5 video + Canvas overlay demo.
- `src/components/Dashboard.jsx` – Recharts-based analytics.
- `src/components/AuthForms.jsx` – Login/Register with real-time validation.
- `src/components/Cart.jsx` – Reusable cart modal.
- `src/components/Navbar.jsx` & `src/components/ThemeToggle.jsx` – UI shell.
- `src/mock/api.js` – Swap with your Laravel endpoints.

## Security Notes

- Use **HTTPS**, **CSRF protection** (if using cookies), **JWT expiry + refresh**, **rate limiting** on auth routes.
- Validate all inputs on the backend. Never trust client-only validation.
- Use **Stripe/Razorpay** for payments; the prototype just simulates checkout.

## Performance Tips

- Host media on a CDN; stream with adaptive bitrates (HLS/DASH).
- Code-split pages and lazy-load heavy components.
- Debounce API calls, cache course lists, and paginate long lists.
- Offload heavy tasks to background queues (already part of your backend plan).

## License

MIT for demo purposes.
