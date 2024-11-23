# Minesweeper AI

An intelligent agent that plays Minesweeper optimally using propositional logic and inference rules.

## Overview

This AI agent employs knowledge-based reasoning to play Minesweeper with an optimal strategy. It uses:
- Propositional logic to represent the game state
- Logical inference to deduce safe moves and mine locations
- Probability-based decision making for uncertain situations

## Key Features

### Knowledge Representation
- Maintains a knowledge base of logical sentences about mine locations
- Each sentence represents constraints about neighboring cells
- Updates knowledge base after every move using new information

### Inference Engine
- Makes logical deductions by comparing sentences in knowledge base
- Identifies safe moves when cells are proven to be mine-free
- Marks confirmed mines when their locations can be definitively determined

### Strategic Move Selection
1. Prioritizes moves that are proven safe through logical inference
2. When no safe move can be deduced:
   - Calculates probability of mines for all unknown cells
   - Selects the cell with the lowest probability of containing a mine
   - Uses random selection when multiple cells tie for lowest probability

## How It Works

1. **Initial State**: The AI starts with knowledge of the board dimensions and total number of mines.

2. **Game Loop**:
   - Analyzes current board state
   - Updates knowledge base with new information from previous moves
   - Performs logical inference to identify safe moves
   - If no safe moves found, calculates mine probabilities
   - Executes chosen move and processes results

3. **Knowledge Update**:
   - After each move, adds new logical sentences based on revealed numbers
   - Performs inference between new and existing knowledge
   - Updates certain safe cells and mine locations

## Requirements

- Python 3.x
- pygame (for visualization)

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yzaazaa/MinesweeperAgent
cd MinesweeperAgent
python3 -m venv venv
source venv/bin/activate # On Windows use `venv\Scripts\activate`
```
2. Install Dependencies

```bash
pip install -r requirements.txt
```
3. Run the script:
```bash
python runner.py
```

## Implementation Details

### Key Methods

- `add_knowledge()`: Updates the AI's knowledge base after each move
- `make_safe_move()`: Makes a move known to be safe
- `make_random_move()`: Makes a probabilistic move when no safe move is known

### Strategy

The AI follows this decision hierarchy:
1. Make logically proven safe moves if available
2. When uncertain, calculate mine probabilities for remaining cells
3. Choose the cell with lowest mine probability
4. Break ties randomly among lowest probability cells

## Credits

Developed as part of the Harvard CS50's Introduction to Artificial Intelligence with Python course.
