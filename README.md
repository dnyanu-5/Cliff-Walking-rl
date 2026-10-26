# CliffWalking: SARSA vs Q-Learning

Tabular reinforcement learning on the `CliffWalking-v1` environment from [Gymnasium](https://gymnasium.farama.org/), comparing two classic algorithms:

- **SARSA** (on-policy)
- **Q-learning** (off-policy)

## Demo


| SARSA | Q-learning |
|---|---|
| _add video/GIF here_ | _add video/GIF here_ |

## The Environment

The agent walks on a 4 x 12 grid from the start (bottom-left) to the goal (bottom-right). The cliff runs along the bottom edge.

| Event | Reward |
|---|---|
| Every normal step | -1 |
| Stepping into the cliff | -100 (agent returns to start) |

- States: 48
- Actions: 4 (up, right, down, left)

## The Algorithms

Both algorithms use an epsilon-greedy policy and a Q-table of shape `(48, 4)`.

| | SARSA | Q-learning |
|---|---|---|
| Type | On-policy | Off-policy |
| Update target | `r + γ · Q(s', a')` | `r + γ · max Q(s', ·)` |
| Uses next action actually taken? | Yes | No, uses the best action |
| Typical learned path | Safer path, away from the cliff | Shortest path, along the cliff edge |

Update rules:

```
SARSA:      Q(s,a) ← Q(s,a) + α [ r + γ Q(s',a') − Q(s,a) ]
Q-learning: Q(s,a) ← Q(s,a) + α [ r + γ max_a' Q(s',a') − Q(s,a) ]
```

## Hyperparameters

| Parameter | Value |
|---|---|
| Discount factor (gamma) | 0.99 |
| Exploration rate (epsilon) | 0.1 |
| Learning rate (alpha) | 0.5 |
| Episodes | 500 |

## Results

![CliffWalking game](assets/game.PNG)


## Project Structure

```
.
├── README.md
├── SARSA_Cliff_Walking.ipynb
├── Q-Learning_Cliff_Walking.ipynb
├── assets/            # videos, photos
└── requirements.txt
```

## How to Run

```bash
git clone https://github.com/<your-username>/<repo-name>.git
cd <repo-name>
pip install -r requirements.txt
jupyter notebook
```

Open either notebook and run all cells.

`requirements.txt`:

```
gymnasium
numpy
```

## Key Takeaways

- SARSA learns the value of the policy it actually follows, including exploratory mistakes, so it avoids the cliff edge,SARSA takes the safer path.
- Q-learning learns the value of the optimal policy, so it finds the shortest path but falls off the cliff more often during training,Q-learning takes the edge path.

## Author

Dnyaneshwari | [GitHub](https://github.com/dnyanu-5/Cliff-Walking-rl.git) | [LinkedIn](https://www.linkedin.com/in/dnyaneshwari-sonawane-673859313/)
