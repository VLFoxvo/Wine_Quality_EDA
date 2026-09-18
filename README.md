# Wine Quality Exploratory Data Analysis

**A chemistry-driven EDA exploring the relationship between wine composition and quality ratings**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)](https://jupyter.org/)

## 🎯 Project Overview

This project explores the UCI Wine Quality dataset (6,497 wines: 1,599 red + 4,898 white) to understand which chemical parameters influence wine quality. Unlike typical data science approaches, this analysis leverages **domain expertise in bioorganic chemistry** to engineer meaningful features and interpret results through a chemical lens.

**Key approach:** Chemistry-first EDA with focus on:
- Stoichiometric feature engineering (molar concentrations, fermentation completeness)
- Chemical style identification via clustering
- Nonlinear relationship detection
- Honest interpretation of data limitations

## 🔬 Key Findings

### 1. Quality is Weakly Correlated with Individual Chemical Parameters
- **Alcohol content** shows the strongest correlation with quality (ρ ≈ 0.4-0.5)
- **Volatile acidity** negatively impacts quality in red wines (bacterial spoilage indicator)
- No single chemical parameter strongly predicts quality

### 2. Clustering Reveals Chemical Styles, Not Quality Levels
Four distinct clusters identified across both wine types:
- **"Clean Fermentation"** (highest quality): complete fermentation, low volatile acidity
- **"Oxidized/Spoiled"** (lowest quality): low free SO₂, high bound SO₂, bacterial contamination
- **"Sweet/Stopped Fermentation"**: intentional sweet styles, average quality
- **"Full-bodied/Acidic"**: pronounced structure

**Key insight:** Quality is **orthogonal** to chemical style. A wine can be well-made or poorly-made within any style.

### 3. Red and White Wines Have Different Quality Determinants

| Feature | Red Wines | White Wines | Explanation |
|---------|-----------|-------------|-------------|
| Alcohol/density ratio | 0.094 | 0.152 | Wider style diversity in whites |
| Sulphates | 0.067 | - | Phenolic extraction in red winemaking |
| Chlorides | 0.015 | 0.061 | Taste sensitivity in lighter-bodied whites |
| Fermentation completeness | 0.010 | 0.044 | More residual sugar styles in whites |

### 4. Derived Features Outperform Original Features
Four of the top seven predictive features for white wines are chemically derived (fermentation completeness, buffer capacity, sulfur dioxide binding), demonstrating the value of **domain knowledge in feature engineering**.

### 5. Fundamental Limitation
Wine quality **cannot be unequivocally predicted** from chemical composition alone. Quality depends on factors not captured in this dataset: grape variety, terroir, vintage, winemaking techniques, and taster subjectivity.

## 🛠️ Technologies & Methods

- **Data Analysis:** pandas, numpy
- **Visualization:** seaborn, matplotlib
- **Machine Learning:** scikit-learn (KMeans, Random Forest, permutation importance)
- **Statistical Tests:** scipy (Kruskal-Wallis, correlation analysis)
- **Feature Engineering:** Custom chemical transformations (molar concentrations, stoichiometric ratios)

## 📊 Dataset

**Source:** [UCI Machine Learning Repository - Wine Quality](https://archive.ics.uci.edu/ml/datasets/wine+quality)

**Features (11 physicochemical properties):**
- Fixed acidity, volatile acidity, citric acid
- Residual sugar, chlorides
- Free sulfur dioxide, total sulfur dioxide
- Density, pH, sulphates
- Alcohol (% vol)

**Target:** Quality score (3-9, rated by sensory assessors)

## 📁 Repository Structure
<pre>
wine-quality-eda/
├── README.md                       # This file
├── wine_quality_eda.ipynb          # Main analysis notebook
├── requirements.txt                # Python dependencies
├── winequality-red.csv             # Red wine dataset (1,599 samples)
├── winequality-white.csv           # White wine dataset (4,898 samples)
├── images/
│   ├── correlation_heatmaps.png    # Red vs White correlation matrices
│   ├── cluster_profiles.png        # Cluster centroids visualization
│   ├── feature_importance.png      # Random Forest permutation importance
│   └── alcohol_distribution.png    # Multimodal alcohol distribution
└── LICENSE                         # MIT License
</pre>
## 🚀 Getting Started

### Prerequisites
- Python 3.8 or higher
- Jupyter Notebook or JupyterLab

### Installation

1. **Clone the repository:**
```bash
git clone https://github.com/YOUR_USERNAME/wine-quality-eda.git
cd wine-quality-eda
```

2. **Create virtual environment (recommended):**
```bash
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
```

3. **Install dependencies:**
```bash
pip install -r requirements.txt
```

4. **Launch Jupyter:**
```bash
jupyter notebook wine_quality_eda.ipynb
```

## 📈 Notebook Sections

1. **Data Loading & Overview** — Initial exploration of red and white wine datasets
2. **Red vs White: Fundamental Differences** — Distribution comparison, type-specific patterns
3. **Correlation Analysis** — Spearman correlations by wine type, identification of collinear features
4. **Feature Engineering** — Molar conversions, fermentation completeness, buffer capacity, sulfur dioxide binding
5. **Multivariate Exploration** — Parallel coordinates, cluster analysis (KMeans), quality distribution
6. **Feature Importance** — Random Forest permutation importance, handling collinearity
7. **Results & Discussion** — Key findings, type-specific patterns, practical implications
8. **Limitations** — Dataset constraints, missing contextual data, inherent unpredictability of quality
9. **Conclusions** — Answers to key research questions

## 🎓 Chemical Insights

This analysis demonstrates how **domain expertise** enhances data science:

- **Stoichiometric reasoning:** Fermentation completeness calculated from ethanol/acetic acid stoichiometry
- **Equilibrium chemistry:** SO₂ binding ratio reflects oxidative stress through carbonyl binding
- **Acid-base chemistry:** Buffer capacity derived from total acidity and pH
- **Microbial spoilage:** Volatile fraction identifies acetic acid bacteria contamination

## 🔍 Reproducibility

All analysis is reproducible:
- Fixed random seeds (`random_state=42`)
- Explicit data transformations
- Documented feature engineering steps
- Version-controlled code and data

## 📚 References

- Cortez, P., et al. (2009). *Modeling wine preferences by data mining from physicochemical properties.* Decision Support Systems, 47(4), 547-553.
- Jackson, R.S. (2008). *Wine Science: Principles and Applications.* Academic Press.
- Waterhouse, A.L., et al. (2016). *Understanding Wine Chemistry.* Wiley.

## 🤝 Contributing

Contributions welcome! Areas for improvement:
- Additional feature engineering (interaction terms, polynomial features)
- Alternative clustering methods (DBSCAN, hierarchical clustering)
- Deep learning approaches (autoencoders, neural networks)
- Integration of external data (weather, soil composition)

## 📄 License

This project is licensed under the MIT License — see the LICENSE file for details.

## 👨‍🔬 Author

**Vladimir Lisitskiy**

Background in bioorganic chemistry (Novosibirsk State University, Institute of Chemical Biology and Fundamental Medicine). Transitioning from academic research to data science with focus on cheminformatics and scientific computing.

**Contact:** [vl.foxvo@gmail.com](mailto:vl.foxvo@gmail.com) | [GitHub](https://github.com/VLFoxvo)

## 🙏 Acknowledgments

- UCI Machine Learning Repository for the dataset
- The data science community for open-source tools and tutorials
- My mentors and colleagues for feedback and discussions

---

**Note:** This project is part of my portfolio demonstrating the transition from chemistry research to data science. For more projects, visit [my GitHub profile](https://github.com/VLFoxvo).
