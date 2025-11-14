# CyberGuard - Quick Start Guide

## ✅ Backend is Running!

Your CyberGuard API is now running at **http://localhost:8000**

### Test the API

1. **Open your browser** and visit:
   - API Documentation: http://localhost:8000/docs
   - Health Check: http://localhost:8000/health

2. **Test threat detection** using curl or Postman:
```bash
curl -X POST http://localhost:8000/api/threats/analyze ^
  -H "Content-Type: application/json" ^
  -d "{\"content\": \"Click here to verify your account now!\", \"platform\": \"discord\"}"
```

3. **View recent threats**:
```bash
curl http://localhost:8000/api/threats/recent
```

## 🎨 Start the Frontend

Open a **new terminal** and run:

```bash
cd frontend
npm install
npm run dev
```

Then visit **http://localhost:5173** to see the dashboard!

## 📦 Current Setup

You're running the **simplified version** which uses:
- ✅ FastAPI backend (running)
- ✅ Pattern-based threat detection
- ✅ Mock data for testing
- ⏳ ML models (optional - requires additional setup)

## 🚀 Add Full AI Capabilities (Optional)

To enable advanced ML-powered threat detection:

```bash
# This will take some time and requires ~5GB disk space
pip install torch transformers scikit-learn
```

Then run the full version:
```bash
python src/main.py
```

## 🔧 What's Working Now

- ✅ REST API endpoints
- ✅ Threat analysis (pattern-based)
- ✅ Dashboard statistics
- ✅ Analytics trends
- ✅ CORS enabled for frontend

## 📚 API Endpoints

- `GET /` - API info
- `GET /health` - Health check
- `POST /api/threats/analyze` - Analyze content for threats
- `GET /api/threats/recent` - Get recent threats
- `GET /api/analytics/dashboard` - Dashboard stats
- `GET /api/analytics/trends` - Threat trends

## 🛠️ Next Steps

1. **Start the frontend** (see above)
2. **Explore the API docs** at http://localhost:8000/docs
3. **Test threat detection** with different content
4. **Optional**: Install ML libraries for advanced detection
5. **Optional**: Set up PostgreSQL database for persistence

## 💡 Tips

- The simplified version uses mock data - perfect for testing the UI
- API auto-reloads when you make code changes
- Check `DEPLOYMENT.md` for production setup
- See `README.md` for full feature list

## 🐛 Troubleshooting

**Port already in use?**
```bash
# Change port in src/main_simple.py (line with port=8000)
```

**Frontend can't connect?**
```bash
# Make sure backend is running on port 8000
# Check CORS settings in src/main_simple.py
```

## 📞 Need Help?

- Check the API docs: http://localhost:8000/docs
- Review the code in `src/main_simple.py`
- See full documentation in `README.md`
