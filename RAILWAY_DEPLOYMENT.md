# Railway Deployment Guide (Alternative to Render)

## 🚀 Railway vs Render

**Railway** is a great alternative to Render with similar features:
- ✅ Node.js support
- ✅ WebSocket support
- ✅ Environment variables
- ✅ GitHub integration
- ✅ Free tier available

## 📋 Railway Deployment Steps

### Step 1: Sign Up
1. Go to https://railway.app
2. Sign up with GitHub account
3. Verify your email

### Step 2: Create New Project
1. Click "New Project"
2. Select "Deploy from GitHub repo"
3. Choose your repository
4. Select "Deploy Now"

### Step 3: Configure Backend
1. **Set Root Directory**: `server`
2. **Add Environment Variables**:
   ```
   NODE_ENV=production
   CLIENT_URL=https://your-frontend-domain.vercel.app
   ```
3. **Deploy** - Railway will auto-detect Node.js

### Step 4: Get Backend URL
1. Go to "Settings" tab
2. Copy the generated domain
3. It will look like: `https://your-app-production.up.railway.app`

### Step 5: Deploy Frontend to Vercel
1. Go to https://vercel.com
2. Import your GitHub repo
3. Add environment variable:
   ```
   NEXT_PUBLIC_SOCKET_URL=https://your-app-production.up.railway.app
   ```
4. Deploy

### Step 6: Update Backend CORS
1. Go back to Railway dashboard
2. Update `CLIENT_URL` with your Vercel domain
3. Redeploy

## 🔧 Railway Configuration

### Environment Variables
```env
NODE_ENV=production
CLIENT_URL=https://your-frontend-domain.vercel.app
```

### Build Settings
- **Framework**: Auto-detected (Node.js)
- **Build Command**: `npm install`
- **Start Command**: `npm start`

## 🚨 Railway vs Render Differences

| Feature | Railway | Render |
|---------|---------|--------|
| Free Tier | ✅ Available | ✅ Available |
| WebSocket | ✅ Supported | ✅ Supported |
| Auto-deploy | ✅ Yes | ✅ Yes |
| Custom Domain | ✅ Yes | ✅ Yes |
| Sleep Time | ❌ No sleep | ⏰ 15min sleep |

## 💡 Railway Advantages

1. **No Sleep**: Services don't sleep like Render
2. **Faster Deploy**: Usually faster than Render
3. **Better UI**: More intuitive dashboard
4. **Auto-scaling**: Better performance

## 🔍 Troubleshooting Railway

### Common Issues:
- **"Build failed"**: Check package.json in server folder
- **"Service not found"**: Verify root directory is `server`
- **"WebSocket error"**: Check environment variables

### Railway Logs:
1. Go to your project
2. Click "Deployments"
3. Click on latest deployment
4. Check "Logs" tab

## 🎯 Quick Migration from Render

If you're switching from Render to Railway:

1. **Export environment variables** from Render
2. **Create new Railway project**
3. **Import same GitHub repo**
4. **Set same environment variables**
5. **Update Vercel environment variable**
6. **Test connection**

## 📞 Railway Support

- **Documentation**: https://docs.railway.app
- **Discord**: https://discord.gg/railway
- **Email**: support@railway.app 