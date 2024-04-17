# Statistical-and-Machine-Learning-Approaches-for-Portfolio-Optimization
Six portfolio optimization strategies were considered, plus one benchmark. We considered methods relying both in ML and common statistical procedures; and we run an out-of-sample back-test for each strategy. Through performance metric calculations, we determine that ML methods significantly improve returns, but not always increase the Sharpe Ratio. 

The portfolio optimization models were run on daily data of 110 stocks from the NASDAQ from the period of 2000 until April 2020.

## Overview
You can find an overview of the project by reading the paper (to be published soon) in the link: .........  (you can also check the first basic draft which is a report of the project in paper format uploaded as a PDF in this repository)

Note: it is better to clone the repository or download the files. The "Preview" method of Github is not optimal for understading the code, and it does not detect the sections of the notebook as I divided them when coding.

## Downloading the Data
The first step to reproduce this project is to download the folder with the data of the NASDAQ. This is a huge Kaggle Dataset with data of both stocks and ETFs. For my analysis, I used the data of stocks only. If you are using Google Colab or Jupyter notebook, you can upload the data to your environment and then copy the path to load the data. Note that this data contains CSV files of more than 5000 stocks. The first notebook cleans this data, and filters the stocks and the stock information that is necessary for the analysis carried out. The CSV files contain daily price data from several different time periods (since they emerged until they were left out or until April 2020).

Data downloaded from: https://www.kaggle.com/datasets/jacksoncrow/stock-market-dataset?resource=download

Alternatively, this repository contains the cleaned data, as exported from the first notebook (read steps below) as a CSV file. If you want to skip straight to the models and the back-testing algorithm, use this data (export_data.csv) and start from the second notebook.

## Steps of the Code
Start by Data Processing and EDA notebook code. This is the first programming step, where the data was fully prepared for running of the models and back-tests. From this notebook, one can export the cleaned CSV file, which serves as an input for the other three notebooks.

I then moved on to creating the Classical Mean Variance notebook. There, I experimented through different concepts of the Mean Variance portfolio theory, and then came up with an efficient way of back-testing the first portfolio models. 

I reused many of the functions from the Classical Mean Variance code for the Mean Variance with ML (Machine Learning) notebook. Here, I again experimented first with the new models incorporated to the analysis: Facebook Prophet and GARCH. Then, I performed hyperparameter tuning of Facebook Prophet, and I manually studied how to configure the best parameters for the GARCH model. Afterwards, I ran a similar back-test than before but with the new models. In this notebook, beware of the fact that the Maximum Sharpe Ratio strategy back-testing algorithm has a really long computational time, because the Facebook Prophet and the GARCH model are both ran at every iteration (rebalancing period).

Finally, move on to Risk Parity and Hierarchical Risk Parity notebook. This notebook is easier to follow and I included some more explanation of the models, as well as plots. I also reuse some code for the back-testing algorithm.

## More Details
The first notebook starts by webscraping the tickers of the consitituent stocks of the NASDAQ 100 and NASDAQ Financial-100 indices. We do this to filter the stocks we want to select. We also delete the data we do not need, keeping only the Adjusted Closed prices of each of the selected stocks, and the Dates (daily). We cleaned the data, using Pandas package, calculated daily returns and reorganized the data such that every column is one stock. We dropped the columns (stocks) that had NaN values. This is how we end up with 110 stocks.

The models are Naive Mean Variance (MVP portfolio and Max Sharpe Portfolio); Mean Variance with Machine Learning (estimate expected returns with Facebook Prophet forecasts, and forecast volatility using GARCH), Risk Parity and Hierarchical Risk Parity. The notebooks explain thoroughly the steps of the code, so refer to them for more details.

## About Rolling Sharpe Ratios and Annualizing Methods for Statistical Measures
The large values of the Sharpe Ratios occur as a consequence of the annualizing method, which has been found to greatly overstate Sharpe Ratios unless certain distributional assumptions hold. We still chose to use this annualizing method because of its simplicity, and because the purpose of this study is comparative, not suggestive of an investment advice. As long as we use the same annualizing method for each strategy, the comparison of them remains consistent and robust.

For more about annualizing methods, see _The Statistics of Sharpe Ratios_ by Andrew W. Lo (2002) in the _Financial Analysts Journal_; _Annual Risk Measures and Related Statistics_ by Arno Weber (2017) from _Ortec Finance_.
