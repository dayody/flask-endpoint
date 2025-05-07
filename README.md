Data API Endpoints
A Flask-based REST API for retrieving company information, stock market data, historical market data, and analytical insights.

Features
Company Information Endpoint: Retrieve detailed company information by symbol
Stock Market Data Endpoint: Fetch real-time stock market data
Historical Market Data Endpoint: Get historical market data for a specified date range
Analytical Insights Endpoint: Perform comprehensive analysis of company data

4.	Install dependencies:
pip install -r requirements.txt
Usage
1.	Start the Flask application:
python app.py
2.	The API will be available at http://localhost:5000/api/v1/

API Endpoints
1. Company Information
Endpoint: /api/v1/company/<symbol>
Method: GET
Description: Retrieves detailed company information from Yahoo Finance.
Example Request:
GET http://localhost:5000/api/v1/company/AAPL Example Response:
json
{
  "status": "success",
  "data": {
    "name": "Apple Inc.",
    "summary": "Apple Inc. designs, manufactures, and markets smartphones, personal computers, 
    "industry": "Consumer Electronics",     "sector": "Technology",
    "website": "https://www.apple.com",
    "employees": 164000,
    "officers": [
      {
        "name": "Timothy D. Cook",
        "title": "Chief Executive Officer & Director"
      },
      {
        "name": "Luca Maestri",
        "title": "Chief Financial Officer & Senior VP"
      }
    ]
  },
  "timestamp": "2025-04-25T12:34:56.789012"
}
 
2. Stock Market Data
Endpoint: /api/v1/stock/<symbol>
Method: GET
Description: Fetches real-time stock market data. Example Request:
GET http://localhost:5000/api/v1/stock/MSFT Example Response:
json
{
  "status": "success",
  "data": {
    "symbol": "MSFT",
    "price": 342.75,
    "open": 340.23,
    "high": 344.88,
    "low": 339.56,
    "volume": 25367800,
    "price_change": 2.52,
    "pct_change": 0.74,
    "market_cap": 2550000000000,
    "market_state": "REGULAR",
    "timestamp": "2025-04-25T12:34:56.789012"
  },
  "timestamp": "2025-04-25T12:34:56.789012" }


4. Historical Market Data
Endpoint: /api/v1/historical/<symbol>
Method: POST
Description: Returns historical market data for a company within a given date range.
Example Request:
POST http://localhost:5000/api/v1/historical/GOOGL
Content-Type: application/json
{
  "start_date": "2025-01-01",
  "end_date": "2025-04-01",
  "interval": "1d"
}
Example Response:
json
{
  "status": "success",   "data": {
    "symbol": "GOOGL",
    "start_date": "2025-01-01",
    "end_date": "2025-04-01",
    "interval": "1d",
    "historical_data": [
      {
        "date": "2025-01-02",
        "open": 142.35,
        "high": 145.67,
        "low": 141.98,
        "close": 144.33,
        "volume": 28976500
      },
      {
        "date": "2025-01-03",
        "open": 144.87,
        "high": 146.22,
        "low": 143.76,
        "close": 145.12,
        "volume": 24567800
      }
    ]
  },
  "timestamp": "2025-04-25T12:34:56.789012"
}

5. Analytical Insights
Endpoint: /api/v1/analysis/<symbol>
Method: POST
Description: Performs a comprehensive analysis of a company based on historical data.
Example Request:
POST http://localhost:5000/api/v1/analysis/AMZN
Content-Type: application/json
{
  "period": 365,
  "type": "advanced"
}
Example Response: 
json
{
  "status": "success",
  "data": {
    "symbol": "AMZN",
    "current_price": 3458.75,
    "period_days": 365,
    "start_date": "2024-04-25",
    "end_date": "2025-04-25",
    "metrics": {
      "avg_price": 3245.87,
      "min_price": 2876.54,
      "max_price": 3598.76,
      "price_range_pct": 25.11,
      "sma_50": 3389.45,
      "sma_200": 3187.23,
      "volatility_annual_pct": 28.76,
      "rsi": 62.45,
      "macd": 15.7823,
      "macd_signal": 10.2356,
      "performance_pct": 18.35
    },
    "insights": {
      "trend": "Bullish",
      "rsi_status": "neutral",
      "macd_signal": "bullish",
      "summary": "Over the past 365 days, AMZN has shown bullish trend with an average price of       "detailed_summary": "AMZN has neutral RSI conditions at 62.45 and shows a bullish MACD si
    }
  },
  "timestamp": "2025-04-25T12:34:56.789012" }
 
Error Handling
All endpoints return appropriate HTTP status codes and error messages in case of failure:
json
{
  "status": "error",
  "message": "No stock data found for symbol: XYZ",
  "timestamp": "2025-04-25T12:34:56.789012"
}
