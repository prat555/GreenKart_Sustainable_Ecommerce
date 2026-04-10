# GreenKart – Sustainable E‑Commerce Platform

Greenkart is a full‑stack e‑commerce app for eco‑friendly products. It offers a clean, fast shopping experience, user‑scoped cart and wishlist, and a Carbon Footprint Tracker to encourage sustainable choices.

![Shizuka Platform](https://img.shields.io/badge/Platform-E--Commerce-green) ![React](https://img.shields.io/badge/React-19-blue) ![Express](https://img.shields.io/badge/Backend-Express-lightgreen) ![MongoDB](https://img.shields.io/badge/Database-MongoDB-darkgreen) ![Tailwind](https://img.shields.io/badge/Styling-Tailwind%20CSS-cyan)

## Key features

- Product browsing with categories, search, featured carousels
- User‑scoped Wishlist and Cart (persisted via backend)
- Buy Now, Add to Cart, and Wishlist actions require sign‑in (redirects to Login)
- Carbon Footprint Tracker (auth‑gated view; shows static demo data for now)
- Polished UI with Tailwind and a consistent gray background (custom `bg-gray-75`)
- Home hero uses an animated eco GIF; Login auto‑scrolls to top on navigation

## Tech stack

- Frontend: React 19, React Router, Tailwind CSS, React Icons, React Multi Carousel, Axios
- Auth: Firebase Authentication (Email/Password + Google)
- Backend: Node.js, Express, MongoDB, Mongoose, CORS, dotenv

## 📁 Project structure

```
GreenKart/
├─ public/
│  ├─ images/
│  └─ index.html
├─ src/
│  ├─ components/
│  ├─ pages/
│  ├─ utils/
│  └─ firebase.js
├─ backend/
│  ├─ config/
│  ├─ models/
│  ├─ routes/
│  └─ server.js
└─ README.md
```

## Auth behavior

- Actions that modify user data (Add to Cart, Wishlist, Buy Now) require authentication.
- If a guest clicks these, they are redirected to `/login`.
- The Login page auto‑scrolls to the top so the form is always visible.
- Carbon Tracker requires sign‑in; when signed in it shows static demo data (no backend writes yet).

## Available scripts

Frontend (root):

- `npm start` – start CRA dev server
- `npm run build` – build for production (note: current script moves build to `src/build`)

Backend (`backend/`):

- `npm start` – start Express server
- `npm run dev` – start with nodemon (if you have it installed)

## API overview

Base URL (dev): `http://localhost:5000`

Products

- `GET /products` – list products (supports `?category=` and `?search=`)
- `GET /products/featured` – featured products
- `GET /products/categories` – dynamic category list

Cart

- `POST /cart/add` – add/increase
- `POST /cart/update` – update quantity or remove (`quantity: 0`)
- `GET /cart/:userId` – get user cart
- `DELETE /cart/remove/:id` – remove item by productId

Wishlist

- `POST /wishlist/toggle` – add/remove
- `GET /wishlist/:userId` – get user wishlist
- `POST /wishlist/remove` – remove specific item

Carbon (experimental; prefixed with `/api/carbon`)

- `GET /api/carbon/profile`
- `GET /api/carbon/dashboard`
- `GET /api/carbon/activities`
- `POST /api/carbon/activity`
- `POST /api/carbon/goal`
- `GET /api/carbon/goals`
- `POST /api/carbon/purchase-impact`

## 📄 License

Licensed under the MIT License – see [LICENSE](./LICENSE).
