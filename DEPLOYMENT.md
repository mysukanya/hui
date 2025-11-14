# CyberGuard Deployment Guide

## Prerequisites

- Python 3.11+
- Node.js 18+
- PostgreSQL 15+
- Redis 7+
- Docker & Docker Compose (optional)

## Local Development

### Backend Setup

```bash
# Create virtual environment
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env with your configuration

# Run database migrations
alembic upgrade head

# Start backend server
python src/main.py
```

### Frontend Setup

```bash
cd frontend

# Install dependencies
npm install

# Start development server
npm run dev
```

## Docker Deployment

```bash
# Build and start all services
docker-compose up -d

# View logs
docker-compose logs -f

# Stop services
docker-compose down
```

## Production Deployment

### Backend (FastAPI)

```bash
# Install production dependencies
pip install gunicorn

# Run with Gunicorn
gunicorn src.main:app -w 4 -k uvicorn.workers.UvicornWorker --bind 0.0.0.0:8000
```

### Frontend (React)

```bash
cd frontend

# Build for production
npm run build

# Serve with nginx or any static file server
```

## Environment Variables

Required environment variables:

- `DATABASE_URL`: PostgreSQL connection string
- `REDIS_URL`: Redis connection string
- `JWT_SECRET`: Secret key for JWT tokens
- `ENCRYPTION_KEY`: Key for data encryption

Optional platform integrations:

- `DISCORD_BOT_TOKEN`: Discord bot token
- `SLACK_BOT_TOKEN`: Slack bot token
- `REDDIT_CLIENT_ID`: Reddit API client ID
- `REDDIT_CLIENT_SECRET`: Reddit API secret

## Security Considerations

1. Use strong, unique secrets for JWT and encryption
2. Enable HTTPS in production
3. Configure CORS properly
4. Implement rate limiting
5. Regular security audits
6. Keep dependencies updated

## Monitoring

- Health check endpoint: `GET /health`
- Metrics endpoint: `GET /metrics` (if enabled)
- WebSocket status: `ws://localhost:8000/ws/threats`

## Scaling

- Use load balancer for multiple backend instances
- Redis for session management and caching
- PostgreSQL read replicas for analytics
- CDN for frontend assets
