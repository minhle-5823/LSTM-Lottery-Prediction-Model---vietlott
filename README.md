# Vietlott Mega 6/45 Lottery Prediction: LSTM with Attention Mechanism

## 🎯 Project Overview

This project presents a sophisticated approach to predicting the winning numbers of the Vietlott Mega 6/45 lottery, which is treated as a complex time series forecasting problem.

The model utilizes a **Long Short-Term Memory (LSTM)** network, enhanced with an **Additive Attention Mechanism (Self-Attention)**, to better capture the weighted dependencies and patterns within the historical draw data. It incorporates advanced feature engineering, including One-Hot Encoding, recent number frequency, and a "coldness" factor (Draws Since Last Drawn - DSLD).

## ✨ Model Performance Highlights

  - **Architecture:** Sequential LSTM layers with a Self-Attention layer (`AdditiveAttention`) to focus on the most relevant past draws.
  - **Input Features:** A dense feature vector (`10 timesteps` x `135 features`) combining:
    1.  One-Hot encoded draw numbers.
    2.  Normalized frequency of each number in the last 5 draws (`T_LOOKBACK = 5`).
    3.  Normalized "coldness" of each number.
  - **Evaluation:** The model is evaluated based on the **Hit-Rate** (number of correctly predicted winning numbers out of 6) on the validation and test sets.

## ⚙️ How to Run the Project (Using the `.ipynb` file)

Since only the Jupyter Notebook file (`Mega_predictor_LSTM_model_(attention).ipynb`) is uploaded, you must first prepare the data file and install the necessary libraries.

### 1\. Prerequisites and Setup

You need to have Python installed. All dependencies can be installed via `pip`:

```bash
pip install pandas numpy tensorflow scikit-learn matplotlib
```

### 2\. Input Data File Format

The notebook requires one specific CSV file in the same directory to run successfully:

| File Name | Description |
| :---: | :---: |
| `mega_6_45.csv` | Historical drawing results. |

**`mega_6_45.csv` Format:**

The CSV file must contain the following columns that match the code logic:

  - **`num_1`, `num_2`, `num_3`, `num_4`, `num_5`, `num_6`**: These six columns must contain the six winning numbers of each draw (ranging from 1 to 45).
  - **Other columns** (e.g., `date`, `draw_id`) are optional but should exist if the notebook references them.

| draw\_id | date | num\_1 | num\_2 | num\_3 | num\_4 | num\_5 | num\_6 |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| 0001 | 01/01/2020 | 5 | 10 | 22 | 34 | 40 | 45 |
| 0002 | 03/01/2020 | 1 | 8 | 15 | 28 | 39 | 42 |
| ... | ... | ... | ... | ... | ... | ... | ... |

**Action Required:** Create this `mega_6_45.csv` file with your historical data and place it in the same directory as the notebook.

### 3\. Execution Steps

1.  **Open the Notebook:** Launch Jupyter Notebook or use Google Colab/Kaggle to open `Mega_predictor_LSTM_model_(attention).ipynb`.
2.  **Run Cells:** Execute all cells sequentially. The notebook will perform the following actions:
      * Load and preprocess the data, calculating advanced features.
      * Construct the LSTM + Attention model.
      * Train the model for **20 epochs** (`epochs=20`).
      * Save the trained model as `best_lottery_lstm_model_attention.keras`.
      * Display the training history plots (Loss and Hit Count).
      * Perform the final evaluation on the separated Test Set.
      * Execute **Section 8** to load the saved model and predict the numbers for the next subsequent draw based on the latest 10 draws.

## 🧑‍💻 Repository Structure

```
.
├── Mega_predictor_LSTM_model_(attention).ipynb # Main source code
├── mega_6_45.csv                             # Required Input Data (User must provide)
└── best_lottery_lstm_model_attention.keras   # Output: Saved model file after training
```

## 📄 License

This project is for academic and personal research purposes.

