# 🚀 Deployment Checklist for Vercel + Render

## ✅ Pre-Deployment Checklist

- [ ] Code is pushed to GitHub
- [ ] Environment variables are ready
- [ ] Both Vercel and Render accounts created

## 🔧 Backend (Render) Setup

- [ ] Go to https://render.com
- [ ] Create New Web Service
- [ ] Connect GitHub repository
- [ ] Set Root Directory: `server`
- [ ] Set Build Command: `npm install`
- [ ] Set Start Command: `npm start`
- [ ] Add Environment Variables:
  - [ ] `NODE_ENV=production`
  - [ ] `CLIENT_URL=https://your-frontend-domain.vercel.app`
- [ ] Deploy and get backend URL

## 🎨 Frontend (Vercel) Setup

- [ ] Go to https://vercel.com
- [ ] Import GitHub repository
- [ ] Framework: Next.js
- [ ] Add Environment Variable:
  - [ ] `NEXT_PUBLIC_SOCKET_URL=https://your-backend-url.onrender.com`
- [ ] Deploy and get frontend URL

## 🔄 Final Configuration

- [ ] Update backend `CLIENT_URL` with actual Vercel domain
- [ ] Redeploy backend
- [ ] Test WebSocket connection

## 🧪 Testing

- [ ] Open frontend URL
- [ ] Check browser console for errors
- [ ] Test teacher functionality
- [ ] Test student functionality
- [ ] Test real-time features

## 🚨 Common Issues

- [ ] CORS errors → Check `CLIENT_URL` in backend
- [ ] WebSocket connection failed → Check `NEXT_PUBLIC_SOCKET_URL`
- [ ] Build failed → Check package.json scripts
- [ ] Service not found → Check Render root directory

## 📞 Support

If issues persist:
1. Check Render logs
2. Check Vercel build logs
3. Verify environment variables
4. Test with browser console open 