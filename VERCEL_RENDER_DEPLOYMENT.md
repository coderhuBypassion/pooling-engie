# Vercel + Render Deployment Guide

## 🚀 Quick Deployment (No Docker)

### Step 1: Deploy Backend to Render

1. **Go to [Render.com](https://render.com)** and sign up/login
2. **Create New Web Service**
3. **Connect your GitHub repository**
4. **Configure the service:**
   - **Name**: `polling-backend`
   - **Root Directory**: `server` (important!)
   - **Runtime**: `Node`
   - **Build Command**: `npm install`
   - **Start Command**: `npm start`
   - **Plan**: Free (or paid if needed)

5. **Add Environment Variables:**
   ```
   NODE_ENV=production
   CLIENT_URL=https://your-frontend-domain.vercel.app
   ```

6. **Deploy** - Render will give you a URL like: `https://your-app.onrender.com`

### Step 2: Deploy Frontend to Vercel

1. **Go to [Vercel.com](https://vercel.com)** and sign up/login
2. **Import your GitHub repository**
3. **Configure the project:**
   - **Framework Preset**: Next.js
   - **Root Directory**: `/` (leave empty)
   - **Build Command**: `npm run build`
   - **Output Directory**: `.next`

4. **Add Environment Variable:**
   ```
   NEXT_PUBLIC_SOCKET_URL=https://your-backend-url.onrender.com
   ```

5. **Deploy** - Vercel will give you a URL like: `https://your-app.vercel.app`

### Step 3: Update Backend Environment Variable

1. **Go back to Render dashboard**
2. **Update the `CLIENT_URL` environment variable:**
   ```
   CLIENT_URL=https://your-frontend-domain.vercel.app
   ```
3. **Redeploy the backend**

## 🔧 Environment Variables Summary

### Render (Backend)
```env
NODE_ENV=production
CLIENT_URL=https://your-frontend-domain.vercel.app
```

### Vercel (Frontend)
```env
NEXT_PUBLIC_SOCKET_URL=https://your-backend-url.onrender.com
```

## 📁 Repository Structure for Render

Make sure your repository structure looks like this:
```
pooling-engie/
├── server/
│   ├── server.js
│   ├── package.json
│   └── .env (create this)
├── app/
├── src/
├── package.json
└── next.config.mjs
```

## 🚨 Important Notes for Render

1. **Root Directory**: Set to `server` in Render dashboard
2. **Free Tier Limitations**: 
   - Service sleeps after 15 minutes of inactivity
   - First request after sleep takes 30-60 seconds
   - Consider upgrading for production use
3. **WebSocket Support**: Render supports WebSockets on paid plans

## 🚨 Important Notes for Vercel

1. **Environment Variables**: Must start with `NEXT_PUBLIC_` to be accessible in browser
2. **WebSocket Client**: Works perfectly with Render backend
3. **Free Tier**: Very generous, no sleep issues

## 🔍 Troubleshooting

### Backend Issues (Render)
- **"Service not found"**: Check root directory is set to `server`
- **"Build failed"**: Check package.json has correct start script
- **"WebSocket connection failed"**: Check CORS and environment variables

### Frontend Issues (Vercel)
- **"Socket connection failed"**: Check `NEXT_PUBLIC_SOCKET_URL` environment variable
- **"Build failed"**: Check Next.js configuration

### Connection Issues
- **"CORS error"**: Verify `CLIENT_URL` in backend matches frontend URL exactly
- **"WebSocket timeout"**: Render free tier may have sleep issues

## 💡 Pro Tips

1. **Use Custom Domains**: Both Vercel and Render support custom domains
2. **Monitor Logs**: Check Render logs for backend issues
3. **Test Locally**: Test with production URLs before going live
4. **Backup**: Keep local environment files for reference

## 🎯 Quick Test

After deployment, test the connection:
1. Open browser console on your Vercel app
2. Check for WebSocket connection errors
3. Try creating a poll as teacher
4. Join as student from another browser tab 