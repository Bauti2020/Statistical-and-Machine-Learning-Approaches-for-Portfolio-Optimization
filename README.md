# Statistical-and-Machine-Learning-Approaches-for-Portfolio-Optimization
Six portfolio optimization strategies were considered, plus one benchmark. We considered methods relying both in ML and common statistical procedures; and we run an out-of-sample back-test for each strategy. Through performance metric calculations, we determine that ML methods significantly improve returns, but not always increase the Sharpe Ratio.

## Steps of the Code
Start by Data Processing and EDA notebook code. This is the first programming step, where the data was fully prepared for running of the models and back-tests. From this notebook, one can export the cleaned CSV file, which serves as an input for the other three notebooks.

I then moved on to creating the Classical Mean Variance notebook. There, I experimented through different concepts of the Mean Variance portfolio theory, and then came up with an efficient way of back-testing the first portfolio models. 

I reused many of the functions from the Classical Mean Variance code for the Mean Variance with ML (Machine Learning) notebook. Here, I again experimented first with the new models incorporated to the analysis: Facebook Prophet and GARCH. Then, I performed hyperparameter tuning of Facebook Prophet, and I manually studied how to configure the best parameters for the GARCH model. Afterwards, I ran a similar back-test than before but with the new models. In this notebook, beware of the fact that the Maximum Sharpe Ratio strategy back-testing algorithm has a really long computational time, because the Facebook Prophet and the GARCH model are both ran at every iteration (rebalancing period).

Finally, move on to Risk Parity and Hierarchical Risk Parity notebook. This notebook is easier to follow and I included some more explanation of the models, as well as plots. I also reuse some code for the back-testing algorithm.
