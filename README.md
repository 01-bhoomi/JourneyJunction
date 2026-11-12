# JourneyJunction 🧭

JourneyJunction is a full-stack **travel stay listing website** built with Node.js, Express and MongoDB. Users can browse places to stay, see each location on an interactive map, sign up and log in, add their own listings with photos, and leave reviews and ratings.

## 🔗 Live Demo

Check out the live project here: **[journeyjunction-ueyp.onrender.com](https://journeyjunction-ueyp.onrender.com/listings)**

> The app runs on a free hosting plan, so the first visit after some time can take up to a minute to load.

## ✨ Features

- 🔐 **User Authentication**: Sign up, log in and log out with Passport.js. Passwords are stored in hashed form.
- 🏠 **Listings**: Create, view, edit and delete listings. Only the owner of a listing can edit or delete it.
- 🖼️ **Image Uploads**: Listing photos are uploaded to Cloudinary using Multer.
- 🗺️ **Interactive Maps**: The location of each listing is found with the Mapbox API and shown on a map with a marker.
- ⭐ **Reviews and Ratings**: Logged-in users can add a review with a rating from 1 to 5. Only the author of a review can delete it.
- ✅ **Server-side Validation**: All form data is checked with Joi before it is saved.
- 💬 **Flash Messages**: Clear success and error messages after every action.
- 🔒 **Persistent Sessions**: Login sessions are stored in MongoDB, so users stay logged in.
- 🎨 **Server-rendered Pages**: Pages are built with EJS and EJS-Mate layouts, styled with Bootstrap.

## 🛠️ Tech Stack

| Category | Technology |
|---|---|
| Runtime | Node.js (v22.14.0) |
| Framework | Express.js 5 |
| Database | MongoDB Atlas with Mongoose |
| Templating | EJS and EJS-Mate |
| Styling | Bootstrap and custom CSS |
| Authentication | Passport.js (local strategy) and passport-local-mongoose |
| File Storage | Cloudinary and Multer |
| Maps | Mapbox (geocoding and Mapbox GL JS) |
| Validation | Joi |
| Sessions | express-session and connect-mongo |
| Other | connect-flash, method-override, dotenv |

## 📁 Project Structure

```
JourneyJunction/
├── controllers/     # Logic for each route (listings, reviews, users)
├── init/            # Sample data and database seeding script
├── models/          # Mongoose schemas (Listing, Review, User)
├── public/          # CSS and client-side JavaScript (map, form checks)
├── routes/          # Route definitions
├── utils/           # Helpers (custom error class, async wrapper)
├── views/           # EJS pages, layouts and partials
├── app.js           # Main entry point
├── cloudConfig.js   # Cloudinary setup
├── middleware.js    # Login, owner and validation checks
├── schema.js        # Joi validation schemas
├── vercel.json      # Vercel settings
├── LICENSE
└── package.json
```

## 🗃️ Data Models

| Model | Main fields |
|---|---|
| **Listing** | title, description, image, price, location, country, geometry (map coordinates), owner, reviews |
| **Review** | comment, rating (1 to 5), author, createdAt |
| **User** | username, email, password (hashed) |

## 🔗 Main Routes

| Method | Route | What it does | Access |
|---|---|---|---|
| GET | `/listings` | Show all listings | Everyone |
| GET | `/listings/new` | Show the new listing form | Logged in |
| POST | `/listings` | Create a listing | Logged in |
| GET | `/listings/:id` | Show a listing with its map and reviews | Everyone |
| GET | `/listings/:id/edit` | Show the edit form | Owner |
| PUT | `/listings/:id` | Update a listing | Owner |
| DELETE | `/listings/:id` | Delete a listing | Owner |
| POST | `/listings/:id/reviews` | Add a review | Logged in |
| DELETE | `/listings/:id/reviews/:reviewId` | Delete a review | Review author |
| GET / POST | `/signup` | Create an account | Everyone |
| GET / POST | `/login` | Log in | Everyone |
| GET | `/logout` | Log out | Logged in |

## ⚙️ Prerequisites

Before you begin, make sure you have:

- [Node.js](https://nodejs.org/) (v22.14.0 recommended)
- A [MongoDB Atlas](https://www.mongodb.com/cloud/atlas) cluster, or a local MongoDB
- A [Cloudinary](https://cloudinary.com/) account for image uploads
- A [Mapbox](https://www.mapbox.com/) account for maps

## 🚀 Getting Started

### 1. Clone the repository

```bash
git clone https://github.com/01-bhoomi/JourneyJunction.git
cd JourneyJunction
```

### 2. Install dependencies

```bash
npm install
```

### 3. Set up environment variables

Create a `.env` file in the main folder and add:

```env
ATLASDB_URL=your_mongodb_connection_string
SECRET=your_session_secret
CLOUD_NAME=your_cloudinary_cloud_name
CLOUD_API_KEY=your_cloudinary_api_key
CLOUD_API_SECRET=your_cloudinary_api_secret
MAP_TOKEN=your_mapbox_access_token
```

> ⚠️ Never upload your `.env` file to GitHub. It is already listed in `.gitignore`.

### 4. Run the app

```bash
npm start
```

Then open:

```
http://localhost:8080
```

## 🔑 Environment Variables

| Variable | Description |
|---|---|
| `ATLASDB_URL` | MongoDB connection string |
| `SECRET` | Secret key used to protect login sessions |
| `CLOUD_NAME` | Cloudinary cloud name |
| `CLOUD_API_KEY` | Cloudinary API key |
| `CLOUD_API_SECRET` | Cloudinary API secret |
| `MAP_TOKEN` | Mapbox public access token |

## 🌐 Deployment

### Render

1. Push the project to GitHub and connect the repository to Render.
2. Set the **Build Command** to `npm install`.
3. Set the **Start Command** to `npm start`.
4. Add all the environment variables above, and also `NODE_ENV` with the value `production`.
5. In MongoDB Atlas, open **Network Access** and allow access from `0.0.0.0/0`.
6. Click **Deploy**.

### Vercel

Import the repository, add the same environment variables and deploy. The included `vercel.json` sends all requests to `app.js`.

## 🧯 Troubleshooting

| Problem | What to check |
|---|---|
| Deploy fails right away | The start command should be `npm start` and all environment variables must be set |
| Internal Server Error | Open the hosting logs. Usually a variable is missing or the database is not reachable |
| Database does not connect | Allow your host in Atlas Network Access and check `ATLASDB_URL` |
| Map or photo upload fails | Check `MAP_TOKEN` and the Cloudinary keys |

## 📄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

## 👤 Author

Developed by [Bhoomi Singh](https://github.com/01-bhoomi)
