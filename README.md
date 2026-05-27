# 📈 Hidden Markov Model: Stock Market Regime Detection

Financial markets do not behave uniformly; they constantly shift between different phases or "regimes," such as periods of steady growth (Bull markets), rapid crashes and high volatility (Bear markets), and sideways movement (Stagnant markets). 

This project utilizes **Hidden Markov Models (HMM)**—a powerful unsupervised machine learning technique—to automatically detect these hidden market states using historical stock data.

## 🎯 Project Objectives
1. **Feature Engineering:** Transform raw daily stock prices (Dow Jones Industrial Average) into stationary, meaningful features.
2. **Model Training:** Build a statistical model from scratch to learn the rules of the market.
3. **State Decoding:** Classify every trading day into a specific market regime.
4. **Visualization:** Analyze and prove the mathematical differences in volatility and returns across the detected regimes.

## 🧠 Methodology & Algorithms

Instead of relying on pre-packaged HMM libraries, this project implements the core mathematics from scratch for maximum numerical stability:

* **Feature Selection:** The model observes three key indicators:
  * `returns`: Daily percentage change in closing price.
  * `range`: A proxy for daily volatility `(High - Low) / Open`.
  * `vol_chg`: Daily percentage change in trading volume.
* **Initialization:** K-Means clustering is used to establish the initial emission means before training begins.
* **Scaled Baum-Welch Algorithm:** An Expectation-Maximization (EM) algorithm used to train the HMM. A *scaled* version is implemented to prevent the numerical underflow errors common when computing long sequences of probabilities.
* **Log-Viterbi Algorithm:** A dynamic programming algorithm used to find the most likely sequence of hidden states (regimes) given the observed sequence of market data.

## 🛠️ Tech Stack
* **Language:** Python 3
* **Data Manipulation:** `pandas`, `numpy`
* **Statistics & Math:** `scipy.stats.multivariate_normal`
* **Machine Learning:** `scikit-learn` (KMeans)
* **Visualization:** `plotly.graph_objects`, `plotly.subplots`

## 📊 Results & Visualization
The notebook concludes with an interactive **Violin Plot** generated via Plotly. This plot visually proves the model's accuracy by grouping the daily data by their newly discovered hidden states. 

You can clearly observe how the detected **Bear Market** state exhibits massive, wide-ranging volatility compared to the tighter, positive distribution of the **Bull Market** state.

## 🚀 How to Run

1. Clone this repository to your local machine:
   ```bash
   git clone [https://github.com/AbobakrSafwat/hmm-market-regime-detection.git](https://github.com/AbobakrSafwat/hmm-market-regime-detection.git)
