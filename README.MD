# README

## Overview

Streamlit appication that runs a market wizard Q&A bot using Groq for hosted inference, 'llama3-70b-8192' as the LLM, and Yahoo Finance as the source of financial data.  

The application has a few functions that the model uses to perform calculations and to respond to common queries that a user might ask.  


## Installation

### Prerequisites
- Python 3.9
- Docker (for deployment)

### Setup

1. **Clone the repository**:
    ```bash
    git clone https://github.com/sidmohan0/yahoofinancewizard.git
    cd yahoofinancewizard
    ```

2. **Install required Python packages**:
    ```bash
    pip install -r requirements.txt
    ```

3. **Set up environment variables**:
    - Create a `.env` file in the project root.
    - Add your Groq API key:
        ```
        GROQ_API_KEY=your_groq_api_key_here
        ```

4. **Run the application**:
    ```bash
    streamlit run app.py
    ```

## Usage

1. **Ask about current stock prices**:
    - Example: "What's the current price of Meta stock?"

2. **Request historical stock prices**:
    - Example: "Show me the historical prices of Apple vs Microsoft stock over the past 6 months."

## Deployment with Docker

1. **Build the Docker image**:
    ```bash
    docker build -t yahoofinancewizard:latest -f app/Dockerfile .
    ```

2. **Run the Docker container**:
    ```bash
    docker run -d -p 8501:8501 yahoofinancewizard:latest
    ```

3. **Access the application**:
    - Open your browser and go to `http://localhost:8501`.


### Functions

1. **`get_stock_info(symbol, key)`**:
    - Retrieves specific information about a stock based on the provided key.
    
2. **`get_historical_price(symbol, start_date, end_date)`**:
    - Fetches historical stock prices for the given date range.

3. **`plot_price_over_time(historical_price_dfs)`**:
    - Plots the historical prices for comparison using Plotly.

4. **`call_functions(llm_with_tools, user_prompt)`**:
    - Handles user prompts, invokes relevant tools, and generates responses.


## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

For any issues or contributions, please feel free to create a pull request or open an issue in the repository.