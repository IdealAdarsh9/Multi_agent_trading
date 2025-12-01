🏦 The Algorithmic Trading Council

A Multi-Agent Financial Decision System powered by Google Gemini

"If you ask a single AI for financial advice, it might hallucinate. If you ask a Council, they debate until they find the truth."

📖 Overview

The Algorithmic Trading Council is an autonomous AI agent system designed to simulate a professional institutional trading desk. Built for the Google AI Agents Intensive Capstone (Enterprise Track), it solves the problem of "single-agent bias" in financial modeling.

Instead of a single bot making a "Buy" decision, this project orchestrates five specialized agents with conflicting goals (e.g., a risk-averse manager vs. an aggressive technical trader) to debate, critique, and vote on a trade.

🏗️ Architecture

This project uses a Hierarchical "Mixture of Agents" Pattern:

graph TD
    User[User Input: Ticker NVDA] --> Orch[Orchestrator]
    
    subgraph "Analyst Tier (Parallel)"
        Orch --> Fund[🔵 Fundamental Agent]
        Orch --> Tech[📈 Technical Agent]
        Orch --> Sent[📰 Sentiment Agent]
    end
    
    Fund --> Risk[🛡️ Risk Manager]
    Tech --> Risk
    Sent --> Risk
    
    Risk -->|Veto or Approval| Head[⚖️ Head Trader]
    Fund --> Head
    Tech --> Head
    Sent --> Head
    
    Head --> Final[💰 Final Verdict JSON]


🤖 The Agents

Agent

Role

Personality

Fundamental Analyst

Value Investor

Obsessed with P/E ratios, revenue growth, and long-term health.

Technical Analyst

Day Trader

Ignores news; focuses strictly on RSI, MACD, and chart patterns.

Sentiment Analyst

Market Psychologist

Reads news headlines to gauge "Fear" vs "Greed."

Risk Manager

The Gatekeeper

The "Devil's Advocate." Can veto a trade if volatility is too high, regardless of potential profit.

Head Trader

Decision Maker

Synthesizes all reports and issues the final Buy/Sell/Hold command.

✨ Key Features

Type-Safe Communication: Agents communicate strictly via structured JSON (using Python Dataclasses and Enums), preventing the "rambling" text issues common in chatbots.

Adversarial Logic: The system includes a negative feedback loop (The Risk Manager) to reduce hallucinations and false positives.

Weighted Consensus: The Head Trader uses a weighted algorithm (Fundamental > Technical > Sentiment) to break deadlocks.

Explainable AI: Every decision outputs a rationale field, explaining why the trade was chosen.

🚀 Installation & Usage

Prerequisites

Python 3.10 or higher

A Google Cloud API Key (for Gemini)

1. Clone the Repository

git clone [https://github.com/YourUsername/Algorithmic-Trading-Council.git]([https://github.com/IdealAdarsh9/Multi_agent_trading.git])
cd Algorithmic-Trading-Council


2. Install Dependencies

pip install -r requirements.txt


(Note: Main dependency is google-generativeai)

3. Set your API Key

You can set it as an environment variable or paste it directly in the config section of the script.

export GEMINI_API_KEY="your_api_key_here"


4. Run the Council

python stock_prediction_agent.py


📊 Example Output

When running the simulation for NVIDIA (NVDA):

{
  "TICKER": "NVDA",
  "FINAL_DECISION": "HOLD",
  "CONFIDENCE": 85.0%,
  "RATIONALE": "Fundamental signals are strong due to AI chip demand, but Technicals indicate the stock is overextended (RSI 72). Risk Manager advises caution due to regulatory scrutiny.",
  "ACTION_PLAN": {
      "stop_loss": 128.50,
      "target_price": 145.00,
      "position_size": "Small"
  }
}


📂 Project Structure
├── stock_prediction_agent.py   # The main application code
├── requirements.txt            # Python dependencies
├── README.md                   # Project documentation
└── assets/                     # Images and diagrams
