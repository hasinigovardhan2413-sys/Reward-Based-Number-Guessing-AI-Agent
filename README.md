# Reward-Based Number Guessing AI Agent

## Overview
This project implements an AI Agent based on the Perceive → Think → Act → Repeat cycle.

The AI agent uses Binary Search to efficiently guess a number between 1 and 100 while maintaining a reward and penalty score.

## Features
- Perceive → Think → Act → Repeat architecture
- Binary Search strategy
- Reward mechanism
- Penalty mechanism
- Performance scoring

## Technologies Used
- Python

## Reward System
- Correct Guess: +100
- Wrong Guess: -5
- Each Attempt: -1
- Solved within 5 attempts: +20
- More than 10 attempts: -20
