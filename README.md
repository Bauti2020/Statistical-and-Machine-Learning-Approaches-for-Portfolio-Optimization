# Statistical-and-Machine-Learning-Approaches-for-Portfolio-Optimization
Six portfolio optimization strategies were considered, plus one benchmark. We considered methods relying both in ML and common statistical procedures; and we run an out-of-sample back-test for each strategy. Through performance metric calculations, we determine that ML methods significantly improve returns, but not always increase the Sharpe Ratio. These 6 strategies were evaluated across 3 scenarios

The portfolio optimization models were run on daily data of 111 stocks from the NASDAQ from the period of 2000 until December 2019, for the Base Scenario. For the Variation 1 Scenario, the models were run on daily data of 91 stocks from 1995-2020 (not including 2020). 20 Stocks were excluded due to missing values. For the Variation 2, the models were run from 1995-2020 for those 91 stocks plus from 2000-2020 for those 20 stocks excluded before. This way, we study also the sensitivity of the models to different training data.

## Overview
You can find an overview of the project by reading the report in this repository, but this report does not include the scenarios and is a simpler version of this research project. There is currently a more thorough and sophisticated paper version of this project under review for journal publication. The latest draft of this paper can be provided upon request.

Note: it is better to clone the repository or download the files. The "Preview" method of Github is not optimal for understading the code, and it does not detect the sections of the notebook as I divided them when coding.

## Downloading the Data
The first step to reproduce this project is to download the folder with the data of the NASDAQ. This is a huge Kaggle Dataset with data of both stocks and ETFs. For my analysis, I used the data of stocks only. If you are using Google Colab or Jupyter notebook, you can upload the data to your environment and then copy the path to load the data. Note that this data contains CSV files of more than 5000 stocks. The first notebook cleans this data, and filters the stocks and the stock information that is necessary for the analysis carried out. The CSV files contain daily price data from several different time periods (since they emerged until they were left out or until April 2020).

Data downloaded from: https://www.kaggle.com/datasets/jacksoncrow/stock-market-dataset?resource=download

## Steps of the Code
Start by Data Processing and EDA notebook code. This is the first programming step, where the data was fully prepared for running of the models and back-tests. From this notebook, one can export the cleaned CSV files, which serves as an input for the other notebooks.

I then moved on to creating the Classical Mean Variance notebook. There, I experimented through different concepts of the Mean Variance portfolio theory, and then came up with an efficient way of back-testing the first portfolio models. There is one of these notebooks for each Scenario.

I reused many of the functions from the Classical Mean Variance code for the Mean Variance with ML (Machine Learning) notebooks. Here, I again experimented first with the new models incorporated to the analysis: Facebook Prophet and GARCH. Then, I performed hyperparameter tuning of Facebook Prophet, and I manually studied how to configure the best parameters for the GARCH model. Afterwards, I ran a similar back-test than before but with the new models. In these notebooks, beware of the fact that the Maximum Sharpe Ratio strategy back-testing algorithm has a really long computational time, because the Facebook Prophet and the GARCH model are both ran at every iteration (rebalancing period). There is one of these notebooks for each Scenario.

Finally, move on to Risk Parity and Hierarchical Risk Parity notebook. These notebooks are easier to follow and I included some more explanation of the models, as well as plots. I also reuse some code for the back-testing algorithm. There is one of these notebooks for each Scenario.

## More Details
The first notebook starts by webscraping the tickers of the consitituent stocks of the NASDAQ 100 and NASDAQ Financial-100 indices. We do this to filter the stocks we want to select. We also delete the data we do not need, keeping only the Adjusted Closed prices of each of the selected stocks, and the Dates (daily). We cleaned the data, using Pandas package, calculated daily returns and reorganized the data such that every column is one stock. We dropped the columns (stocks) that had NaN values. This is how we end up with 110 stocks.

The models are Naive Mean Variance (MVP portfolio and Max Sharpe Portfolio); Mean Variance with Machine Learning (estimate expected returns with Facebook Prophet forecasts, and forecast volatility using GARCH), Risk Parity and Hierarchical Risk Parity. The notebooks explain thoroughly the steps of the code, so refer to them for more details.
