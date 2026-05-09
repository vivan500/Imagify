# IMAGIFY

IMAGIFY is an AI image generation web application featuring user authentication, a credit-based generation model, and payment integration with Razorpay and Stripe. Users can register/login, purchase credits, and generate images from text prompts using the Clipdrop Text-to-Image API.

## Features

- User registration and login
- JWT-protected backend routes
- Credit balance system for image generation
- AI image creation from text prompts
- Payment flow via Razorpay and Stripe
- MongoDB persistence for users and transactions
- Modern React + Vite frontend with Tailwind CSS

## Tech Stack

- Frontend: React, Vite, Tailwind CSS, React Router, Axios, Framer Motion
- Backend: Node.js, Express, MongoDB, Mongoose
- Authentication: JWT
- Payments: Razorpay and Stripe
- AI Image API: Clipdrop Text-to-Image

## Repository Structure

- `client/` — React frontend
- `server/` — Express backend
- `server/configs/` — MongoDB connection config
- `server/controllers/` — route controllers
- `server/middlewares/` — auth middleware
- `server/models/` — Mongoose schemas
- `server/routes/` — API routes

## Setup

### Prerequisites

- Node.js 18+ / npm
- MongoDB instance or Atlas cluster
- Clipdrop API key
- Razorpay credentials
- Stripe secret key

### Install dependencies

```bash
cd client
npm install

cd ../server
npm install
```

### Environment variables

Create a `.env` file inside the `server/` folder with the following values:

```env
MONGODB_URI=<your-mongodb-connection-string>
JWT_SECRET=<your-jwt-secret>
CLIPDROP_API=<your-clipdrop-api-key>
RAZORPAY_KEY_ID=<your-razorpay-key-id>
RAZORPAY_KEY_SECRET=<your-razorpay-key-secret>
STRIPE_SECRET_KEY=<your-stripe-secret-key>
CURRENCY=INR
PORT=4000
```

> Note: `MONGODB_URI` is used with `/ai-image` in the connection string. Do not include the database name if you want to preserve the current path behavior.

## Running the App

Start the backend server:

```bash
cd server
npm run server
```

Start the frontend app:

```bash
cd client
npm run dev
```

Then open the Vite URL shown in the terminal (usually `http://localhost:5173`).

## API Endpoints

### Auth & User

- `POST /api/user/register` — register a new user
- `POST /api/user/login` — login and receive JWT token
- `GET /api/user/credits` — get current user credit balance (protected)
- `POST /api/user/pay-razor` — create Razorpay order for credits (protected)
- `POST /api/user/verify-razor` — verify Razorpay payment
- `POST /api/user/pay-stripe` — create Stripe checkout session for credits (protected)
- `POST /api/user/verify-stripe` — verify Stripe payment

### Image Generation

- `POST /api/image/generate-image` — generate AI image from prompt (protected)

## Notes

- The backend middleware expects the JWT token to be provided in request headers as `token`.
- Users start with a default credit balance of `5`.
- Each image generation consumes one credit.
- Payment plans are defined in the backend controller and can be updated there.

## Development

- Frontend dev server: `cd client && npm run dev`
- Backend dev server with nodemon: `cd server && npm run server`
- Build frontend: `cd client && npm run build`
- Preview frontend build: `cd client && npm run preview`
- Lint frontend: `cd client && npm run lint`

## License

This project does not include a license by default.
