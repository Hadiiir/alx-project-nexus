# MarketMood AI - Stock Market Sentiment Analysis Platform 📈🤖

![Project Banner](https://via.placeholder.com/1200x400?text=MarketMood+AI+-+Smart+Investing+through+Sentiment+Analysis)

## Table of Contents
- [Project Overview](#project-overview-)
- [Key Features](#key-features-)
- [Technical Architecture](#technical-architecture-)
- [Installation](#installation-)
- [API Documentation](#api-documentation-)
- [Deployment](#deployment-)
- [Screenshots](#screenshots-)
- [Contributing](#contributing-)
- [License](#license-)

## Project Overview 🎯
MarketMood AI is an intelligent investment platform that analyzes news sentiment to generate stock recommendations. By combining NLP with market data, we help investors make data-driven decisions based on market emotions.

**Core Value Proposition**:  
"Quantify market emotions to predict stock movements before they happen"

## Key Features ✨

### Backend Services
- ✅ JWT Authentication (Register/Login/Logout)
- 📊 Stock Market Data API
- 📰 News Aggregation with Sentiment Scoring
- 🤖 AI-Powered Recommendations (BUY/SELL/HOLD)
- 📈 Portfolio Tracking
- ⚡ Redis Caching for Performance
- 🔄 Celery Background Tasks

### Frontend Components
- 📱 Responsive Dashboard
- 📉 Interactive Portfolio Charts
- 🗞️ News Feed with Sentiment Indicators
- 🔔 Personalized Recommendations
- ⚙️ User Profile Management

## Technical Architecture 🧱

### Backend Stack
| Component          | Technology               |
|--------------------|--------------------------|
| Framework          | Django REST Framework    |
| Database           | PostgreSQL               |
| Authentication     | JWT (SimpleJWT)          |
| NLP Library        | TextBlob/VADER           |
| Task Queue         | Celery + Redis           |
| API Docs           | Swagger (drf-yasg)       |
| Deployment         | Render/Railway           |

### Frontend Stack
| Component          | Technology               |
|--------------------|--------------------------|
| Framework          | Next.js                  |
| Styling            | Tailwind CSS             |
| State Management   | SWR                      |
| HTTP Client        | Axios                    |
| Deployment         | Vercel                   |

## Database Schema 🗃️

```ascii
┌───────────────┐       ┌───────────────┐       ┌───────────────┐
│    User       │       │   Portfolio   │       │    Stock      │
├───────────────┤       ├───────────────┤       ├───────────────┤
│▪ id (UUID)    │◄──────┤▪ user_id      │──────▶│▪ id (UUID)    │
│▪ username     │       │▪ stock_id     │       │▪ symbol       │
│▪ email        │       │▪ shares       │       │▪ name         │
│▪ risk_profile │       └───────────────┘       │▪ current_price│
│▪ created_at   │                               └───────────────┘
└───────────────┘                                       ▲
                                                        │
                                                        │
┌───────────────┐                                       │
│ NewsArticle   │       ┌────────────────┐             │
├───────────────┤       │ SentimentScore │             │
│▪ id (UUID)    │       ├────────────────┤             │
│▪ title        │──────▶│▪ stock_id      │─────────────┘
│▪ content      │       │▪ score         │
│▪ published_at │       │▪ mood_label    │
└───────────────┘       └────────────────┘

Key Models:
- **User**: Investor profiles and credentials
- **Stock**: Market data (symbol, price, etc.)
- **NewsArticle**: Financial news content
- **SentimentScore**: NLP analysis results
- **Portfolio**: User investment tracking
- **Recommendation**: AI-generated suggestions

## Installation 🛠️

### Backend Setup
```bash
# Clone repository
git clone https://github.com/Hadiiir/alx-project-nexus.git
cd backend

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows

# Install dependencies
pip install -r requirements.txt

# Environment variables
cp .env.example .env
# Edit .env with your credentials

# Run migrations
python manage.py migrate

# Start server
python manage.py runserver