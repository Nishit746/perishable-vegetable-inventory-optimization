# A Simulation Model for Inventory Management of Perishable Vegetables with Last In First Out Consumption Pattern

## Overview

Perishable inventory systems face a critical trade-off between maintaining product availability and minimizing wastage. In vegetable retail operations, uncertainty in customer demand combined with short product shelf lives often results in either stockouts or excessive spoilage. Traditional experience-based ordering methods used by small retailers frequently lead to suboptimal inventory decisions.

This project develops a **Discrete Event Simulation (DES) framework** for optimizing inventory policies in perishable vegetable retail systems operating under stochastic demand conditions. Using real-world retailer data, the framework models inventory movement, product expiry, lost sales, replenishment decisions, and customer purchasing behavior to identify inventory policies that maximize profitability while reducing waste.

The work was conducted as part of an internship research project and later will be presented at a conference hosted by Mahindra University.

---

## Research Motivation

Inventory planning for perishable products remains one of the most challenging problems in operations research and supply chain management.

Unlike non-perishable products, vegetables have:

* Limited shelf life
* High demand uncertainty
* Significant spoilage risk
* Customer preference for fresher products
* Strong SKU-level variability

Over-ordering increases expiry losses, while under-ordering results in lost sales and reduced customer satisfaction. Therefore, inventory policies must carefully balance availability and wastage.

This study investigates whether simulation-based inventory optimization can improve retailer profitability while realistically representing actual retail operations.

---

## Research Contributions

This work introduces:

* SKU-level stochastic demand modelling
* Distribution fitting using Kolmogorov–Smirnov goodness-of-fit testing
* Discrete Event Simulation of perishable inventory systems
* LIFO (Last-In First-Out) customer selection behavior modelling
* Multi-metric simulation validation framework
* Inventory policy optimization under uncertainty
* Real-world case study involving 21 vegetable SKUs
* Policy recommendation framework based on validated simulation models

---

## Methodology

The overall workflow of the study is illustrated below:

```text
Historical Retail Data
           │
           ▼
 Demand Distribution Fitting
           │
           ▼
 Stochastic Demand Generation
           │
           ▼
 Discrete Event Simulation
           │
           ▼
 Validation Framework
           │
           ▼
 Inventory Policy Evaluation
           │
           ▼
 Optimal Policy Selection
```

---

## Dataset

The dataset was collected through interviews and operational observations from a local vegetable retailer.

### Dataset Characteristics

* 21 vegetable SKUs
* Historical daily demand observations
* Daily expiry quantities
* Daily lost sales
* Cost price per kilogram
* Selling price per kilogram
* Shelf life information
* Lead times
* Inventory policy parameters

---

## Demand Modelling

Customer demand was modelled as a stochastic process.

The following candidate probability distributions were evaluated:

* Normal Distribution
* Gamma Distribution
* Uniform Distribution
* Triangular Distribution
* Beta Distribution
* Exponential Distribution
* Lognormal Distribution

Parameters were estimated from historical observations and goodness-of-fit was evaluated using the Kolmogorov–Smirnov (K-S) test.

### Distribution Fitting Results

* 10 SKUs best fit Gamma distributions
* 7 SKUs best fit Normal distributions
* Remaining SKUs followed Beta, Uniform, or Triangular distributions

These fitted distributions served as stochastic demand generators within the simulation model.

---

## Discrete Event Simulation Framework

A Discrete Event Simulation (DES) model was developed in Python to replicate daily retail operations.

### Daily Events

1. Inventory arrival
2. Demand generation
3. Demand fulfilment
4. Lost sales recording
5. Expiry handling
6. Profit calculation
7. Replenishment decision

### Simulation Characteristics

* Simulation horizon: 60 days
* Multiple independent replications
* SKU-level inventory tracking
* Shelf-life-based expiry modelling
* Lost sales accounting
* Inventory replenishment scheduling

---

## LIFO Inventory Consumption Behaviour

Most inventory models assume FIFO consumption.

However, practical observations in vegetable retail suggest customers prefer fresher produce and often select newly displayed stock.

Therefore, this study adopts a **Last-In First-Out (LIFO)** inventory consumption pattern to better represent real-world customer purchasing behaviour.

This feature significantly improves realism in modelling perishable retail systems.

---

## Inventory Policies Evaluated

Two commonly used replenishment strategies were investigated.

### Fixed Order Quantity Policy

A constant replenishment quantity is ordered at each review period regardless of current inventory position.

### Target Inventory Policy

Inventory is replenished dynamically to reach a predefined target stock level.

### Candidate Policy Levels

Thirteen policy configurations were evaluated for every vegetable SKU, including:

* Scaled mean demand levels
* Demand percentile levels
* Conservative replenishment policies
* Aggressive replenishment policies

This allows analysis across a broad range of inventory strategies.

---

## Validation Framework

A major contribution of this work is the validation methodology.

Simulation outputs were compared against actual retailer observations using three operational metrics:

### Validation Metrics

* Average Profit
* Average Lost Sales
* Average Expiry

### Statistical Validation

99% confidence intervals were computed for simulation outputs.

A SKU was classified as:

| Category            | Criteria                   |
| ------------------- | -------------------------- |
| Fully Validated     | 3/3 Metrics Match          |
| Partially Validated | 2/3 Metrics Match          |
| Weakly Validated    | 1/3 or Fewer Metrics Match |

Only fully validated vegetables were considered for policy optimization.

---

## Results

### Fully Validated Vegetables

The following vegetables achieved complete validation:

* Pumpkin
* Bitter Gourd
* Brinjal
* Beans
* Madras Cucumber
* Beetroot
* Cabbage
* Pudina
* Onion

### Key Findings

* Overall profit increased by approximately 5%
* Expiry wastage reduced by approximately 90%
* Target Inventory Policies consistently outperformed Fixed Order Policies
* Inventory sensitivity varied significantly across SKUs
* Some vegetables exhibited strong responsiveness to policy changes
* Other vegetables remained relatively stable across policy alternatives

### Practical Insight

The results indicate that perishable inventory systems should not rely on a single replenishment strategy for all products.

Inventory decisions should be made at the SKU level to account for demand variability, perishability, and economic characteristics.

---

## Academic Dissemination

This work was developed during an internship research project and presented at a conference organized by Mahindra University.

The study demonstrates how simulation modelling and inventory optimization techniques can be applied to real-world retail systems with limited historical data and significant uncertainty.

---

## Repository Structure

```text
simulation-based-perishable-inventory-optimization/

├── README.md
│
├── data/
│   └── vegetable_inventory_data.xlsx
│
├── notebooks/
│   └── IITKGP_Internship_Project.ipynb
│
├── src/
│   ├── data_preprocessing.py
│   ├── distribution_fitting.py
│   ├── inventory_simulation.py
│   ├── validation.py
│   ├── policy_optimization.py
│   └── visualization.py
│
├── results/
│   ├── distribution_fits.csv
│   ├── validation_results.csv
│   ├── optimal_policies.csv
│   └── figures/
│
├── paper/
│   ├── Abstract_Pramaan.pdf
│   └── Research_Paper_Draft.pdf
│
├── requirements.txt
├── LICENSE
└── .gitignore
```

---

## Technologies Used

* Python
* Pandas
* NumPy
* SciPy
* Matplotlib
* OpenPyXL
* Jupyter Notebook

---

## Future Work

Potential future extensions include:

* Multi-product capacity constrained optimization
* Reinforcement Learning based ordering policies
* Seasonal demand modelling
* Dynamic pricing strategies
* Multi-echelon supply chain simulation
* Inventory optimization under supplier uncertainty
* Integration with real-time retail analytics systems

---

## Keywords

Inventory Management, Operations Research, Discrete Event Simulation, Stochastic Demand Modelling, Perishable Inventory, Supply Chain Analytics, Retail Optimization, Demand Forecasting, Simulation Modelling, Inventory Policy Optimization, Vegetable Retail Systems.

---

## Citation

If you use this work for academic purposes, please cite the repository and accompanying research paper appropriately.
