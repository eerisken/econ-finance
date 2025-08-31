# Manipulators Association Rules Mining

This project analyzes trading activity in financial markets to identify patterns of coordinated behavior between investors (manipulators) using **association rules mining**.

---

## Overview

- Generates random trade data for rules mining
- Load trade data from a CSV file containing:
  - `buyer_id`, `seller_id`, `symbol`, `price`, `quantity`, `date_time`
- Group trades into **minute-level market baskets** containing all unique investors who traded in that minute.
- Apply **FP-Growth** to find frequent investor sets.
- Generate **association rules** with configurable minimum support and confidence thresholds.
- Visualize the relationships between investors as a **network graph**.

## Network Visualization

![Investor Association Network](investor_network.png)

---

## Requirements

- Python 3.11+
- Libraries:
  - `pandas`
  - `mlxtend`
  - `networkx`
  - `matplotlib`
  - `pyvis` (for interactive visualization, optional)

