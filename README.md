# Algorithmic Trading Council – Monitoring System

This project is an automated multi-agent trading analysis system that continuously monitors a stock ticker, gathers real-time market data, analyzes signals through multiple AI agents, and produces a final trading recommendation.

## 📌 Overview
The system uses three cooperating AI agents:
1. Technical Analysis Agent  
2. News Sentiment Agent  
3. Final Decision Agent  

Data is fetched via Yahoo Finance, and reasoning is performed using Gemini API.

## 🧩 Features
- Real-time stock monitoring  
- AI-driven technical analysis  
- AI news sentiment evaluation  
- A final decision agent combining all signals  
- Continuous monitoring loop (5‑minute cycles)

## 📂 Project Structure
```
Algorithmic_Trading_Council.ipynb
├── Data Models
│   ├── MarketData
│   └── AgentResponse
├── Agents
│   ├── TechnicalAnalysisAgent
│   ├── NewsSentimentAgent
│   └── FinalDecisionAgent
├── Yahoo Finance Fetcher
│   └── get_stock_data()
└── Monitoring Entry Point
    └── run_monitoring_session()
```

## 🔧 Requirements
### Python Packages
yfinance  
google-generativeai  

### Environment Variable
```
export GEMINI_API_KEY="YOUR_KEY_HERE"
```

## 🚀 How to Run
1. Install dependencies:
```
pip install yfinance google-generativeai
```
2. Open the notebook.  
3. Run all cells to start monitoring.

## 📄 License
MIT License
