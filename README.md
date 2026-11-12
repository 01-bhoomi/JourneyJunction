<div align="center">

# 🧭 JourneyJunction

**A full-stack travel stay-listing platform. Discover places, list your own, and share reviews.**

![Node.js](https://img.shields.io/badge/Node.js-22.14-339933?logo=node.js&logoColor=white)
![Express](https://img.shields.io/badge/Express-5-000000?logo=express&logoColor=white)
![MongoDB](https://img.shields.io/badge/MongoDB-Atlas-47A248?logo=mongodb&logoColor=white)
![EJS](https://img.shields.io/badge/Views-EJS-B4CA65)
![License](https://img.shields.io/badge/License-ISC-blue)

[Live Demo](https://journeyjuction.onrender.com/listings) · [Report a Bug](https://github.com/01-bhoomi/JourneyJunction/issues)

</div>

> ⏳ **Note:** On the free hosting tier the server sleeps after inactivity, so the first request can take up to a minute.

---

## 📖 About

JourneyJunction is a server-rendered web app built with **Node.js, Express and MongoDB**, following the **MVC** pattern. Users can browse stays, see each place on an interactive map, sign up, create listings with photo uploads, and leave ratings and reviews.

## ✨ Features

| | Feature | Details |
|---|---|---|
| 🔐 | **Authentication** | Sign up, log in and log out with Passport.js (local strategy), hashed passwords |
| 🏠 | **Listings (CRUD)** | Create, view, edit and delete listings; only the owner can edit or delete |
| 🖼️ | **Image uploads** | Photos stored on Cloudinary through Multer |
| 🗺️ | **Maps** | Location is geocoded with the Mapbox API and shown on a map |
| ⭐ | **Reviews and ratings** | Logged-in users can add reviews; only the author can delete theirs |
| ✅ | **Validation** | Server-side validation with Joi |
| 💬 | **Flash messages** | Clear success and error feedback |
| 🔒 | **Sessions** | Persistent sessions stored in MongoDB (`connect-mongo`) |

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Runtime | Node.js 22 |
| Framework | Express 5 |
| Database | MongoDB Atlas + Mongoose |
| Templating | EJS + EJS-Mate layouts, Bootstrap |
| Auth | Passport.js, passport-local-mongoose |
| Storage | Cloudinary, Multer |
| Maps | Mapbox SDK |
| Validation | Joi |
| Hosting | Render / Vercel |

## 📁 Project Structure

```
JourneyJunction/
├── controllers/      # Request handling logic
├── models/           # Mongoose schemas: Listing, Review, User
├── routes/           # Express routers: listings, reviews, users
├── views/            # EJS templates (layouts, includes, pages)
├── public/           # CSS and client-side JS
├── utils/            # Error class and async wrapper
├── init/             # Database seeding scripts
├── app.js            # App entry point
├── cloudConfig.js    # Cloudinary setup
├── middleware.js     # Auth, ownership and validation middleware
├── schema.js         # Joi schemas
└── vercel.json       # Vercel configuration
```

## 🔗 Main Routes

| Method | Route | Description | Auth |
|---|---|---|---|
| GET | `/listings` | All listings | No |
| GET | `/listings/new` | New listing form | Yes |
| POST | `/listings` | Create a listing | Yes |
| GET | `/listings/:id` | Listing details, map and reviews | No |
| GET | `/listings/:id/edit` | Edit form | Owner |
| PUT / DELETE | `/listings/:id` | Update or delete a listing | Owner |
| POST | `/listings/:id/reviews` | Add a review | Yes |
| DELETE | `/listings/:id/reviews/:reviewId` | Delete a review | Author |
| GET / POST | `/signup`, `/login` | Register and log in | No |
| GET | `/logout` | Log out | Yes |

## 🚀 Getting Started

### Prerequisites
- [Node.js](https://nodejs.org/) 22 or newer
- A [MongoDB Atlas](https://www.mongodb.com/atlas) cluster (or local MongoDB)
- A [Cloudinary](https://cloudinary.com/) account
- A [Mapbox](https://www.mapbox.com/) account

### Setup

```bash
# 1. Clone
git clone https://github.com/01-bhoomi/JourneyJunction.git
cd JourneyJunction

# 2. Install
npm install

# 3. Create a .env file (see below)

# 4. Run
npm start
```

Open **http://localhost:8080**.

### Environment variables

Create a `.env` file in the project root:

```env
ATLASDB_URL=your_mongodb_connection_string
SECRET=your_long_random_session_secret
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
MAP_TOKEN=your_mapbox_public_token
```

> ⚠️ Never commit `.env`. It is already listed in `.gitignore`. Never paste real passwords or keys into code or comments.

### Seed sample data (optional)

```bash
node init/index.js
```

## ☁️ Deployment

Set all the environment variables above (plus `NODE_ENV=production`) on the platform you choose. In MongoDB Atlas, allow the host in **Network Access** (for example `0.0.0.0/0`).

### Render
1. **New → Web Service**, connect this repository.
2. Build command: `npm install`
3. Start command: `npm start`
4. Add the environment variables and deploy.

### Vercel
1. **Add New → Project**, import this repository.
2. Add the environment variables.
3. Deploy. `vercel.json` already routes all requests to `app.js`.

## 🧯 Troubleshooting

| Problem | Fix |
|---|---|
| Deploy fails right away | Make sure the start command is `npm start` and all env variables are set |
| `Internal Server Error` | Check the host logs, usually a missing env variable or Atlas network access |
| Database does not connect | Allow your host's IP in Atlas Network Access and check `ATLASDB_URL` |
| Map or image upload fails | Check `MAP_TOKEN` and the Cloudinary keys |

## 👤 Author

**Bhoomi Singh** · [GitHub @01-bhoomi](https://github.com/01-bhoomi)

## 📄 License

Released under the ISC License.
