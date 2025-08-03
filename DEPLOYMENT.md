# Deployment Guide for Live Polling System

## 🚀 Quick Deployment Options

### Option 1: Docker Compose (Recommended)
```bash
# Clone and setup
git clone <your-repo>
cd pooling-engie

# Create environment files
cp env.example .env.local
cp server/env.example server/.env

# Edit environment variables
# .env.local: NEXT_PUBLIC_SOCKET_URL=https://your-backend-domain.com
# server/.env: CLIENT_URL=https://your-frontend-domain.com

# Deploy with Docker
docker-compose up -d
```

### Option 2: Vercel + Railway/Render

#### Frontend (Vercel)
1. Connect your GitHub repo to Vercel
2. Set environment variable: `NEXT_PUBLIC_SOCKET_URL=https://your-backend-url.com`
3. Deploy

#### Backend (Railway/Render)
1. Connect your GitHub repo to Railway/Render
2. Set environment variables:
   - `NODE_ENV=production`
   - `CLIENT_URL=https://your-frontend-url.com`
3. Deploy

### Option 3: Heroku

#### Backend
```bash
cd server
heroku create your-polling-backend
heroku config:set NODE_ENV=production
heroku config:set CLIENT_URL=https://your-frontend-url.com
git push heroku main
```

#### Frontend
```bash
heroku create your-polling-frontend
heroku config:set NEXT_PUBLIC_SOCKET_URL=https://your-backend-url.com
git push heroku main
```

## 🔧 Environment Variables

### Backend (.env)
```env
PORT=5000
NODE_ENV=production
CLIENT_URL=https://your-frontend-domain.com
```

### Frontend (.env.local)
```env
NEXT_PUBLIC_SOCKET_URL=https://your-backend-domain.com
```

## 🌐 Domain Configuration

### For Custom Domains:
1. **Backend**: Point your domain to your backend hosting service
2. **Frontend**: Point your domain to your frontend hosting service
3. **Update Environment Variables**:
   - Backend: `CLIENT_URL=https://your-frontend-domain.com`
   - Frontend: `NEXT_PUBLIC_SOCKET_URL=https://your-backend-domain.com`

## 🔍 Troubleshooting

### WebSocket Connection Issues
1. **Check CORS**: Ensure backend CORS allows your frontend domain
2. **Check SSL**: WebSockets require HTTPS in production
3. **Check Firewall**: Ensure port 5000 is open on backend server

### Common Errors
- **"WebSocket connection failed"**: Check environment variables and CORS
- **"CORS error"**: Verify CLIENT_URL in backend environment
- **"Socket timeout"**: Check network connectivity and firewall settings

## 📝 Production Checklist

- [ ] Environment variables configured
- [ ] CORS settings updated
- [ ] SSL certificates installed
- [ ] Domain names configured
- [ ] Firewall rules set
- [ ] Monitoring/logging enabled
- [ ] Backup strategy in place

## 🚨 Important Notes

1. **WebSockets require HTTPS** in production
2. **CORS must be properly configured** for cross-origin requests
3. **Environment variables must be set** before deployment
4. **Port 5000 must be accessible** for WebSocket connections
5. **Consider using a database** instead of in-memory storage for production 