# Statistical-and-Machine-Learning-Approaches-for-Portfolio-Optimization
Six portfolio optimization strategies were considered, plus one benchmark. We considered methods relying both in ML and common statistical procedures; and we run an out-of-sample back-test for each strategy. Through performance metric calculations, we determine that ML methods significantly improve returns, but not always increase the Sharpe Ratio. 

The portfolio optimization models were run on data of 110 stocks from the NASDAQ from the period of 2000 until April 2020.

## Overview
You can find an overview of the project by reading the paper uploaded as a PDF file in this repository. This was the culmination of my project.

## Downloading Data
The first step to reproduce this project is to download the folder with the data of the NASDAQ. If you are using Google Colab or Jupyter notebook, you can upload the data to your environment and then copy the path to load the data. Note that this data contains CSV files of more than 5000 stocks. The first notebook cleans this data, and filters the stocks and the stock information that is necessary for the analysis carried out.

## Steps of the Code
Start by Data Processing and EDA notebook code. This is the first programming step, where the data was fully prepared for running of the models and back-tests. From this notebook, one can export the cleaned CSV file, which serves as an input for the other three notebooks.

I then moved on to creating the Classical Mean Variance notebook. There, I experimented through different concepts of the Mean Variance portfolio theory, and then came up with an efficient way of back-testing the first portfolio models. 

I reused many of the functions from the Classical Mean Variance code for the Mean Variance with ML (Machine Learning) notebook. Here, I again experimented first with the new models incorporated to the analysis: Facebook Prophet and GARCH. Then, I performed hyperparameter tuning of Facebook Prophet, and I manually studied how to configure the best parameters for the GARCH model. Afterwards, I ran a similar back-test than before but with the new models. In this notebook, beware of the fact that the Maximum Sharpe Ratio strategy back-testing algorithm has a really long computational time, because the Facebook Prophet and the GARCH model are both ran at every iteration (rebalancing period).

Finally, move on to Risk Parity and Hierarchical Risk Parity notebook. This notebook is easier to follow and I included some more explanation of the models, as well as plots. I also reuse some code for the back-testing algorithm.
