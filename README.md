# 🤖 Reward-Based Number Guessing AI Agent

[![Python](https://img.shields.io/badge/Python-3.7+-blue.svg)](https://www.python.org/)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)
[![Status](https://img.shields.io/badge/Status-Active-brightgreen.svg)]()
[![Contributions Welcome](https://img.shields.io/badge/Contributions-Welcome-brightgreen.svg)](#contributing)

An intelligent AI agent that learns to play a number guessing game through reinforcement learning. The agent improves its strategy over time by receiving rewards for correct guesses and penalties for incorrect ones, using the Perceive → Think → Act → Repeat cycle.
````````````````

## 📋 Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [How It Works](#how-it-works)
- [Installation](#installation)
- [Usage](#usage)
- [Reward System](#reward-system)
- [Results](#results)
- [Future Improvements](#future-improvements)

## 🎯 Overview

This project demonstrates **AI Agent Design** and **Reinforcement Learning** by building an intelligent agent that plays a number guessing game. The agent uses the **Perceive-Think-Act-Repeat (PTAR)** cycle to continuously improve its performance.

**Key Concept**: The agent learns optimal strategies without explicit programming through interaction with the environment!

## ✨ Features

- ✅ **Intelligent Learning**: Agent improves performance over episodes
- ✅ **Binary Search Strategy**: Efficient number guessing algorithm
- ✅ **Reward Mechanism**: Positive reinforcement for good decisions
- ✅ **Penalty System**: Negative reinforcement to avoid bad decisions
- ✅ **Performance Scoring**: Track improvement metrics
- ✅ **PTAR Architecture**: Clean perception-thinking-action cycle
- ✅ **Well-Documented**: Clear code with examples

## 🧠 Architecture: Perceive → Think → Act → Repeat

````````````
┌─────────────────────────────────────────┐
│   PERCEIVE                              │
│   ├─ Current state                      │
│   ├─ Number range                       │
│   └─ Previous rewards                   │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│   THINK                                 │
│   ├─ Analyze information                │
│   ├─ Decide next action                 │
│   └─ Apply strategy (binary search)     │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│   ACT                                   │
│   ├─ Make guess                         │
│   ├─ Receive feedback                   │
│   └─ Collect reward/penalty             │
└──────────────┬──────────────────────────┘
               │
┌──────────────▼──────────────────────────┐
│   REPEAT                                │
│   └─ Loop until goal achieved           │
└─────────────────────────────────────────┘
```

## 🎮 How It Works

### Game Rules:
1. Agent must guess a secret number between 1-100
2. After each guess, receives feedback: "Higher", "Lower", or "Correct"
3. Receives rewards/penalties based on performance
4. Goal: Minimize guesses while maximizing rewards

### Agent Strategy:
The agent uses **Binary Search** strategy:
- Guesses the middle of the remaining range
- Eliminates half the search space with each guess
- Optimal strategy requires ~7 guesses for range 1-100

### Learning Process:
1. **Episode Starts**: New secret number selected
2. **Agent Perceives**: Current state, available actions
3. **Agent Thinks**: Decides best guess using binary search
4. **Agent Acts**: Makes guess, receives feedback
5. **Agent Learns**: Updates knowledge based on reward/penalty
6. **Repeat**: Continue until correct guess or max attempts

## 📦 Installation

### Prerequisites
- Python 3.7 or higher
- pip package manager

### Steps

```bash
# Clone repository
git clone https://github.com/hasinigovardhan2413-sys/Reward-Based-Number-Guessing-AI-Agent.git
cd Reward-Based-Number-Guessing-AI-Agent

# Install dependencies (if any)
pip install -r requirements.txt
```

## 🚀 Usage

### Basic Example

````python
from ai_agent import NumberGuessingAgent

# Create an agent
agent = NumberGuessingAgent(min_num=1, max_num=100)

# Play a single game
score = agent.play_game()
print(f"Game score: {score}")

# Play multiple games
for game in range(5):
    score = agent.play_game()
    print(f"Game {game+1}: Score = {score}")
`````

### Advanced Usage

````python
# Create agent with custom parameters
agent = NumberGuessingAgent(
    min_num=1,
    max_num=100,
    max_attempts=15,
    verbose=True  # Print game details
)

# Play and track statistics
scores = []
attempts = []

for _ in range(10):
    score = agent.play_game()
    scores.append(score)

print(f"Average Score: {sum(scores)/len(scores):.2f}")
print(f"Best Score: {max(scores)}")
print(f"Worst Score: {min(scores)}")
```

## 💰 Reward System

### Scoring Mechanism:

| Action | Reward |
|--------|--------|
| **Correct Guess** | +100 |
| **Wrong Guess** | -5 |
| **Each Attempt** | -1 |
| **Solved in ≤5 attempts** | +20 bonus |
| **Solved in >10 attempts** | -20 penalty |

### Reward Calculation:
```
Total Score = Base Reward + Attempt Penalties + Bonus/Penalties
Total Score = 100 - (attempts × 1) + (bonus if applicable)
```

### Examples:
- **Best Case**: Correct in 1 guess = 100 - 1 + 20 = **119 points** ⭐
- **Good Case**: Correct in 5 guesses = 100 - 5 + 20 = **115 points** ✅
- **Average Case**: Correct in 7 guesses = 100 - 7 = **93 points** 👍
- **Poor Case**: Correct in 15 guesses = 100 - 15 - 20 = **65 points** ⚠️

## 📊 Results & Performance

### Typical Performance:

| Metric | Value |
|--------|-------|
| **Average Guesses** | 6-7 |
| **Success Rate** | ~100% |
| **Average Score per Game** | ~93 points |
| **Best Score Achieved** | 119 points |
| **Learning Curve** | Improves with experience |

### Performance Graph:
```
Score per Game:
130 |     ╱
120 |    ╱
110 |   ╱
100 |  ╱────────────
 90 | ╱
 80 |╱
    └─────────────── Games Played
    1 2 3 4 5 6 7...
```

## 🎓 Learning Concepts

This project teaches:
- ✅ AI Agent Architecture (PTAR cycle)
- ✅ Reinforcement Learning principles
- ✅ Binary Search algorithm
- ✅ Reward-based learning
- ✅ Performance optimization
- ✅ State and action spaces
- ✅ Feedback mechanisms

## 📁 Project Structure

```
Reward-Based-Number-Guessing-AI-Agent/
├── README.md              # This file
├── requirements.txt       # Python dependencies (if any)
├── ai_agent.py           # Main agent implementation
├── game.py               # Game logic
├── main.py               # Entry point
└── results/              # Performance results
    └── scores.txt        # Game scores log
```

## 🔮 Future Enhancements

- [ ] Implement Q-Learning for comparison
- [ ] Add Deep Q-Network (DQN) approach
- [ ] Multiple game environments
- [ ] Agent vs Agent competition
- [ ] Web interface for playing
- [ ] Real-time visualization
- [ ] Machine learning model training
- [ ] Export trained policies
- [ ] Multi-agent learning scenarios

## 💡 Advanced Topics

### Concepts to Explore:
- **Markov Decision Process (MDP)**
- **Q-Learning Algorithm**
- **Policy Gradient Methods**
- **Value Function Approximation**
- **Temporal Difference Learning**
- **Monte Carlo Methods**

### Variations:
- Different reward functions
- Variable number ranges
- Time-based rewards
- Multi-step lookahead

## 🤝 Contributing

Contributions are welcome! Here's how:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/new-feature`)
3. Commit your changes (`git commit -m 'Add new feature'`)
4. Push to the branch (`git push origin feature/new-feature`)
5. Open a Pull Request

## 📄 License

MIT License - See [LICENSE](LICENSE) for details.

## 🙏 Acknowledgments

- Inspired by classic AI agent problems
- Built as part of AI learning journey
- Thanks to the AI/ML community

## 📞 Contact

**Hasini Govardhan**
- 🔗 GitHub: [@hasinigovardhan2413-sys](https://github.com/hasinigovardhan2413-sys)
- 📧 Email: hasinigovardhan2413@gmail.com
- 🤝 Open for collaborations and learning opportunities!

---

⭐ **If you found this project helpful, please star it!** It helps others discover it too.

**Happy Learning! Let's build intelligent agents together! 🚀**
