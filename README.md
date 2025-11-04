# Financial Sentiment Analysis: Integrating News Intelligence with HUL Stock Data

## Project Overview

A production-ready system that analyzes financial news sentiment and correlates it with **_Hindustan Unilever Limited_** (HUL) stock performance. The pipeline processes raw news data, applies financial-domain NLP models, and maps sentiment scores to HUL trading dates for quantitative analysis.

## Business Significance

This system addresses critical challenges in:

- **Quantitative Trading**: Incorporating HUL-specific news sentiment into algorithmic strategies
- **Risk Management**: Early detection of HUL market-moving news events
- **Investment Research**: Systematic analysis of news impact on HUL stock performance
- **Compliance Monitoring**: Tracking HUL media coverage for regulatory reporting

## Data Sources

### HUL Stock Data
- **Source**: Manually downloaded from NSE India website
- **Period**: January 2019 to 2024
- **Frequency**: Daily trading data
- **Content**: Date, Open, High, Low, Close, Volume, and other market indicators

### Financial News Data
- **Coverage**: HUL-specific news articles and market analysis
- **Period**: Corresponding to trading data timeframe
- **Sources**: Economic Times and other financial publications

## Technical Implementation

### Data Pipeline Architecture
```mermaid
graph LR
    H[Raw HUL News Data] --> I[Text Normalization]
    I --> J[Sentiment Analysis]
    J --> K[Date Alignment]
    K --> L[HUL Trading Data Integration]
```


### Core Components

**Data Preprocessing**
- Unicode normalization for text consistency
- HUL-specific date parsing with error handling
- Text combination (title + summary) for comprehensive analysis
- Missing value handling and data validation

**Sentiment Analysis Engine**
- FinBERT model (ProsusAI/finbert) for financial domain specificity
- Batch processing with truncation for efficiency
- Score conversion: negative (-score), neutral (0), positive (+score)
- GPU optimization with PyTorch inference

**Temporal Alignment**
- HUL news-to-trading date mapping with next-available-day logic
- Sentiment aggregation at daily frequency
- Volatility-adjusted normalization using tanh scaling
- Standard deviation-based risk weighting

## Model Specifications

### Financial NLP Stack
- **Base Model**: FinBERT (BERT-based, financial domain pre-trained)
- **Output Classes**: Positive, Negative, Neutral with confidence scoring
- **Processing Speed**: Batch inference with 512-token truncation
- **Domain Adaptation**: Specifically trained on financial corpora

### HUL Data Integration
- **News Features**: HUL-specific published date, title, summary content
- **Trading Data**: HUL daily prices, volume, market indicators (2019-2024)
- **Temporal Resolution**: Daily sentiment aggregation
- **Alignment Logic**: Next available HUL trading day mapping

## Limitations & Enhancements

### Current Scope
- HUL single-stock analysis implementation
- Daily frequency (no intraday HUL sentiment)
- English-language HUL news only
- Historical analysis focus (2019-2024)

---

*Domain: Financial NLP, HUL Stock Analysis, Alternative Data, NSE India*
