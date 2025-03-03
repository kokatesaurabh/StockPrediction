# Stock Market Prediction with LSTM and Candlestick Visualization

## Overview
This project is a machine learning-based stock market prediction system that uses a Long Short-Term Memory (LSTM) neural network to forecast stock prices. It supports multiple Indian stocks (e.g., RELIANCE, TCS, INFY) and provides a user-friendly interface to predict future closing prices for a specified number of days. The predictions are visualized in a professional candlestick chart format, mimicking real stock market platforms, complete with historical data and volume bars.

The project leverages historical stock data (`Open`, `High`, `Low`, `Close`, `Volume`) from a CSV file and predicts future trends, making it a valuable tool for learning about stock price forecasting and financial visualization.

## Features
- **Stock Selection**: Predict prices for stocks like RELIANCE, TCS, INFY, HDFCBANK, and more.
- **Custom Prediction Period**: Choose the number of days to forecast (e.g., 3, 5, 10 days).
- **Candlestick Visualization**: Displays historical and predicted data in a stock market-style candlestick chart with volume bars.
- **LSTM Model**: Uses a trained LSTM neural network for time series prediction.
- **Dark Theme**: Professional dark-themed UI, inspired by trading platforms.

## Dataset
The project uses a custom CSV file (`nse_stock_data_small.csv`) with the following structure:
```
Date,Stock Symbol,Open,High,Low,Close,Volume
2020-01-01 00:00:00,RELIANCE,2810.08,2815.15,2776.51,2779.13,123709
...
```
- **Source**: National Stock Exchange (NSE) data (user-provided).
- **Columns**: `Date`, `Stock Symbol`, `Open`, `High`, `Low`, `Close`, `Volume`.

## Installation
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/kokatesaurabh/stock-market-prediction.git
   cd stock-market-prediction
   ```
2. **Install Dependencies**:
   ```bash
   pip install pandas numpy scikit-learn tensorflow mplfinance matplotlib
   ```
3. **Prepare Data**:
   - Place your `nse_stock_data_small.csv` file in the root directory.
   - Ensure it contains data for the stocks listed in `stock_symbols`.

## Usage
1. **Train the Model (Stages 1-6)**:
   - Run the training script if you haven’t already (see `train_model.py` or earlier stages).
   - Save the model (`stock_model.h5`) and scaler (`scaler.pkl`).
2. **Run Predictions (Stage 7)**:
   ```bash
   python predict_candlestick.py
   ```
   - Input a stock symbol (e.g., `TCS`) and number of days (e.g., `3`).
   - View the candlestick chart and predicted prices.

### Example
```plaintext
Available stocks: ['RELIANCE', 'TCS', 'INFY', 'HDFCBANK', 'HINDUNILVR', 'ICICIBANK', 'KOTAKBANK', 'SBIN', 'LT', 'AXISBANK']
Enter stock symbol to predict: TCS
Enter number of days to predict: 3
```
Output:
- A candlestick chart showing the last 30 days of historical data and 3 predicted days.
- Predicted closing prices printed in the console.

## Project Structure
```
stock-market-prediction/
├── nse_stock_data_small.csv  # Input data file
├── train_model.py           # Stages 1-6: Data prep and model training (optional)
├── predict_candlestick.py   # Stage 7: Prediction and visualization
├── stock_model.h5           # Trained LSTM model (generated after training)
├── scaler.pkl               # MinMaxScaler object (generated after training)
├── README.md                # This file
```

## How It Works
1. **Data Preprocessing**: Normalizes historical stock data using MinMaxScaler.
2. **Model**: A pre-trained LSTM predicts future `Close` prices based on sequences of past data.
3. **Prediction**: Simulates `Open`, `High`, and `Low` for candlesticks using the predicted `Close` (±2% variation).
4. **Visualization**: Uses `mplfinance` to render a candlestick chart with volume bars.

## Limitations
- **Single-Value Prediction**: The LSTM predicts only `Close` prices; `Open`, `High`, and `Low` are approximated.
- **Data Dependency**: Requires sufficient historical data per stock for accurate predictions.
- **Simplistic Volume**: Predicted volume is an average of historical values.

## Future Improvements
- Train the model to predict `Open`, `High`, and `Low` alongside `Close`.
- Integrate real-time data via APIs (e.g., Yahoo Finance).
- Add technical indicators (e.g., moving averages, RSI) to the chart.

## Contributing
Contributions are welcome! Please:
1. Fork the repository.
2. Create a feature branch (`git checkout -b feature/your-feature`).
3. Commit your changes (`git commit -m "Add your feature"`).
4. Push to the branch (`git push origin feature/your-feature`).
5. Open a pull request.

## License
This project is licensed under the MIT License. See [LICENSE](LICENSE) for details.

## Acknowledgments
- Built with Python, TensorFlow, and mplfinance.
- Inspired by stock market analysis tools and trading platforms.



