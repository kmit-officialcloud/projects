# 🚀 Production-Ready Deployment Guide

## Complete Tech Stack Implemented

### Must-Have (✅ All Implemented)
- ✅ **Redis** - Caching layer (5-10x faster queries)
- ✅ **RabbitMQ** - Message queue (optional, uses amqplib)
- ✅ **Bull** - Job queue with Redis backend (emails, notifications)
- ✅ **Pino** - High-performance structured logging
- ✅ **Prometheus** - Metrics collection and monitoring

### Architecture Overview

```
┌─────────────────┐
│   Frontend      │
│  (Optimized)    │
└────────┬────────┘
         │
    ┌────▼─────┐
    │  Server  │
    │  Express │
    └─┬──┬──┬──┘
      │  │  │
┌─────▼──▼──▼──────┐
│ Redis   MongoDB  │
│ Cache   Database │
└──────────────────┘
      │
┌─────▼─────────┐
│  Bull Queue   │
│  Background   │
│  Jobs         │
└───────────────┘
```

## Services Required

### 1. MongoDB (Database)
```bash
# Windows Service or Atlas
net start MongoDB
# Or use MongoDB Atlas cloud
```

### 2. Redis (Cache + Queue Backend)
```bash
# Windows
choco install redis-64
redis-server

# Mac
brew install redis
brew services start redis

# Linux
sudo apt-get install redis-server
sudo systemctl start redis
```

### 3. RabbitMQ (Optional - for distributed systems)
```bash
# Windows
choco install rabbitmq

# Mac
brew install rabbitmq
brew services start rabbitmq

# Linux
sudo apt-get install rabbitmq-server
sudo systemctl start rabbitmq-server
```

## Environment Configuration

Update `.env`:

```env
# Core
NODE_ENV=production
PORT=5000

# Database
MONGO_URI=mongodb://localhost:27017/sociosphere
# Or Atlas: mongodb+srv://<user>:<pass>@<cluster>/sociosphere

# Redis (Required for cache + queues)
REDIS_URL=redis://localhost:6379

# RabbitMQ (Optional)
RABBITMQ_URL=amqp://localhost

# Logging
LOG_LEVEL=info

# JWT
JWT_SECRET=your-super-secret-key-change-this

# Cloudinary
CLOUDINARY_CLOUD_NAME=your_cloud_name
CLOUDINARY_API_KEY=your_api_key
CLOUDINARY_API_SECRET=your_api_secret

# Email
EMAIL_SERVICE=gmail
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password

# Optional Services
GIPHY_API_KEY=your_giphy_key
HF_API_KEY=your_huggingface_key
```

## Production Deployment

### Docker Compose (Recommended)

Create `docker-compose.yml`:

```yaml
version: '3.8'

services:
  mongodb:
    image: mongo:8
    volumes:
      - mongo_data:/data/db
    ports:
      - "27017:27017"
    restart: always

  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data
    ports:
      - "6379:6379"
    restart: always
    command: redis-server --appendonly yes

  rabbitmq:
    image: rabbitmq:3-management-alpine
    ports:
      - "5672:5672"
      - "15672:15672"
    volumes:
      - rabbitmq_data:/var/lib/rabbitmq
    restart: always

  sociosphere:
    build: ./backend
    ports:
      - "5000:5000"
    depends_on:
      - mongodb
      - redis
      - rabbitmq
    environment:
      - NODE_ENV=production
      - MONGO_URI=mongodb://mongodb:27017/sociosphere
      - REDIS_URL=redis://redis:6379
      - RABBITMQ_URL=amqp://rabbitmq
    restart: always

volumes:
  mongo_data:
  redis_data:
  rabbitmq_data:
```

Start with:
```bash
docker-compose up -d
```

### Manual Deployment

1. **Install dependencies:**
```bash
cd backend
npm install --production
```

2. **Start services:**
```bash
# MongoDB
net start MongoDB

# Redis
redis-server

# (Optional) RabbitMQ
rabbitmq-server
```

3. **Run app:**
```bash
npm start
# Or with PM2 for auto-restart:
npm install -g pm2
pm2 start server.js --name sociosphere
pm2 save
pm2 startup
```

## Monitoring & Observability

### 1. Prometheus Metrics
Access at: `http://localhost:5000/metrics`

Metrics include:
- HTTP request duration
- Active connections
- Memory usage
- CPU usage
- Custom app metrics

### 2. Logs (Pino)
- Development: Pretty-printed colored logs
- Production: JSON structured logs (ready for ELK/Logstash)

Example log:
```json
{
  "level": "INFO",
  "time": "2025-12-10T12:00:00.000Z",
  "app": "sociosphere",
  "env": "production",
  "msg": "Server started",
  "protocol": "https",
  "port": 5000
}
```

### 3. Bull Dashboard (Job Queue UI)
```bash
npm install -g bull-board
# Add to server.js for UI at /admin/queues
```

## Performance Features

### Caching Strategy
- **L1**: Redis cache (1-5ms)
- **L2**: MongoDB with indexes (10-50ms)
- **TTL**: 30-60 seconds for dynamic content

### Background Jobs (Bull)
- Email sending (async, retried 3x)
- Notifications (async, retried 2x)
- Analytics events (fire-and-forget)

### Monitoring (Prometheus)
- Request latency percentiles (p50, p95, p99)
- Error rates by endpoint
- Database connection pool stats

## Health Checks

```bash
# App health
curl http://localhost:5000/api/health

# Prometheus metrics
curl http://localhost:5000/metrics

# Redis
redis-cli ping  # Should return PONG

# MongoDB
mongosh --eval "db.runCommand({ping: 1})"

# RabbitMQ
curl http://localhost:15672/api/overview  # UI: user/pass = guest/guest
```

## Deployment Checklist

- [ ] MongoDB running and connected
- [ ] Redis running and connected
- [ ] Environment variables configured
- [ ] SSL certificates (for HTTPS)
- [ ] Cloudinary configured
- [ ] Email service configured
- [ ] Prometheus scraping configured
- [ ] Log aggregation setup (optional)
- [ ] PM2 or Docker for auto-restart
- [ ] Nginx reverse proxy (optional)
- [ ] Firewall rules configured
- [ ] Backups configured

## Scaling Strategy

### Horizontal Scaling
1. **Multiple app instances** with load balancer
2. **Redis** for shared session/cache
3. **Bull queues** for background work distribution
4. **MongoDB replica set** for high availability

### Vertical Scaling
1. Increase Redis memory
2. Increase MongoDB pool size
3. Add more CPU cores
4. Optimize database indexes

## Troubleshooting

### High Memory Usage
- Check Redis memory: `redis-cli INFO memory`
- Reduce cache TTL
- Check for memory leaks: `node --inspect server.js`

### Slow Queries
- Check MongoDB slow query log
- Verify indexes: `db.collection.getIndexes()`
- Monitor with `/metrics` endpoint

### Queue Backlog
- Check Bull dashboard
- Increase worker concurrency
- Check job failure patterns

## Production URLs

- **App**: https://your-domain.com
- **API**: https://your-domain.com/api
- **Metrics**: https://your-domain.com/metrics
- **Health**: https://your-domain.com/api/health

## Support

For issues or questions:
1. Check logs: `pm2 logs sociosphere`
2. Check metrics: `curl http://localhost:5000/metrics`
3. Verify services are running
4. Check environment variables

Your app is now production-ready! 🚀
