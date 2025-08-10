# Deploying the Collectible Tracker

Below are **one-command** deployment instructions for free hosting platforms. You must perform the deploy steps (I cannot host it for you).

## Option A — Deploy to Render (recommended for full server + static client)

1. Create a free account at https://dashboard.render.com
2. Create a new **Web Service** for the server:
   - Connect your git repository (or you can push the `server/` folder to a new GitHub repo).
   - Build Command: `npm install && npm run init-db`
   - Start Command: `npm start`
   - Environment: add `JWT_SECRET` (random string)
3. Create a **Static Site** for the client:
   - Point it to the `client/` directory on GitHub.
   - Build Command: `npm install && npm run build`
   - Publish Directory: `client/build`
4. On the frontend (client), set `REACT_APP_API_URL` to the server URL + `/api` in Render static site environment variables.

Render will provide public URLs for both frontend and backend.

## Option B — Deploy to Railway (server + client in one project)

1. Sign up at https://railway.app
2. Create a new project, import this repository.
3. For server service:
   - Root: `/server`
   - Add Environment Variables: `JWT_SECRET`
   - Commands: `npm install` / `npm start`
4. For client:
   - You can host the client as a static site in Railway, or build and serve from server using express static (optional).
5. Railway provides a public URL.

## Option C — Deploy to Vercel (Frontend) + Railway/Render for Backend

1. Deploy the `client/` folder to Vercel (https://vercel.com/new) — connect your repo and point it at the `client/` directory.
2. Deploy the `server/` folder to Railway or Render (follow above).
3. Set `REACT_APP_API_URL` in Vercel to the backend URL.

## Running locally (quick)
1. Server
   ```
   cd server
   npm install
   npm run init-db
   # create a .env file or copy .env.example and set JWT_SECRET
   node server.js
   ```
2. Client
   ```
   cd client
   npm install
   npm start
   ```
Then open `http://localhost:3000`.

