🚀 The Multi Agent for Trading and Crypto 24/7 Market Monitor powered by Google Gemini"Crypto never sleeps. Neither should your analysis. A multi-agent council that watches the charts so you don't have to."📖 OverviewThe Crypto Sentinel AI is a continuous monitoring agent designed for the Google AI Agents Intensive Capstone. Unlike standard trading bots that simply check prices, this system employs a Council of AI Agents to analyze market structure, news sentiment, and technical indicators in real-time.It runs in a continuous loop, refreshing every 5 minutes to provide disciplined, risk-adjusted signals.🏗️ ArchitectureThis project uses a Cyclic Multi-Agent Pattern with a self-healing API layer:graph TD
    Start[🚀 Init: Auto-Detect Gemini Model] --> Loop
    
    subgraph "Continuous Monitoring Loop (Every 5 Mins)"
        Loop[⏱️ Timer Trigger] --> Data[📡 Market Data Provider]
        Data -->|Price + News| Tech[📈 Technical Analyst]
        Data -->|Headlines| Sent[📰 Sentiment Analyst]
        
        Tech --> Head[⚖️ Head Trader]
        Sent --> Head
        
        Head -->|Final Verdict| Output[🖥️ Terminal Display]
        Output --> Sleep[💤 Sleep 300s]
        Sleep --> Loop
    end
🤖 The CouncilAgentRoleFunctionTechnical AnalystChart ReaderAnalyzes RSI, MACD, and Price Action. Ignores news completely.Sentiment AnalystNews ReaderAnalyzes headlines to gauge "Fear" vs "Greed". Ignores the chart.Head TraderRisk ManagerSynthesizes conflicting reports. If Technicals say "Buy" but Sentiment says "Panic", it orders a HOLD.✨ Key Technical Features1. 🛡️ Self-Healing API LogicThe system automatically detects the best available Google Gemini model.Priority 1: gemini-2.5-flash (Fastest, Newest)Priority 2: gemini-1.5-flash (Stable Fallback)Priority 3: gemini-pro (Legacy Fallback)Benefit: If one model is down or rate-limited, the bot switches automatically without crashing.2. 🚦 Smart Rate LimitingTo respect free-tier API limits, the agents function asynchronously with built-in delays (time.sleep). If a 429 Too Many Requests error occurs, the system pauses and retries intelligently.3. 📡 Real-Time Data PipelineIntegrated with yfinance to fetch live crypto prices and news.Automatically handles ticker symbols (e.g., converts BTC to BTC-USD).Fetches Price, 24h Change, and News Headlines dynamically.🚀 Installation & UsagePrerequisitesPython 3.10 or higherA Google Cloud API Key (for Gemini)1. Clone the Repositorygit clone [https://github.com/YourUsername/Crypto-Sentinel-AI.git](https://github.com/YourUsername/Crypto-Sentinel-AI.git)
cd Crypto-Sentinel-AI
2. Install Dependenciespip install -r requirements.txt
(Dependencies: google-generativeai, yfinance)3. Set your API KeyYou can set it as an environment variable (recommended) or input it when prompted.export GEMINI_API_KEY="your_api_key_here"
4. Run the Sentinelpython crypto_trading_agent.py
📊 Example OutputWhen running the monitor for Ethereum (ETH):==================================================
🚀 CRYPTO SENTINEL AGENT INITIALIZED
==================================================
Enter asset to monitor: ETH

✅ Monitoring ETH started. Press Ctrl+C to stop.

⏱️  TIME: 16:30:00 | 💰 PRICE: $2,745.20 (-1.2%)
--------------------------------------------------
Thinking...
📈 Tech Signal: BUY (RSI: 42 - Oversold Bounce Likely)
📰 News Mood:   Neutral (Uncertainty regarding ETF flows)
🟡 FINAL DECISION: HOLD (Conf: 0.65)
📝 Rationale: Technicals show a potential bounce, but lack of positive sentiment confirmation makes a Buy risky. Waiting for confirmation.

💤 Sleeping for 300 seconds...
📂 Project Structure├── crypto_trading_agent.py   # Main application logic
├── requirements.txt          # Python dependencies
├── README.md                 # Documentation
🔮 Future RoadmapTelegram Integration: Send alerts directly to a Telegram channel.Portfolio Tracking: Track PnL of simulated trades over time.Multi-Asset Mode: Monitor BTC, ETH, and SOL simultaneously.⚠️ DisclaimerThis project is for educational purposes only. The "Trade Signals" generated are simulations based on AI analysis and should not be taken as financial advice. Trading cryptocurrency involves significant risk.
