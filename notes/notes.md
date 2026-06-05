**05/06/2026**

Intially the plan was to compare prediction market odds to bookmakers. Incentivized by the upcoming 2026 world cup, I wanted to check if we see a divergence between bookie odds and polymarket odds and take trades when the difference in odds is greater than 10% and then sell the respective polymarket contract.The first notebook will simply be compared adjusted bookie probabilities to polymarket but we will investigate this market further this is just an introduction. 

This has been tested on 3 specific contracts. When slippage and fees are considered (0.1% per trade) returns quickly decay, though some still outperform buy and hold. While their strategy simply buys the contract when a new minimum has been reached and sells after a given number of days (tested over a range of parameters), this excludes many key markets: US politics, esports, football, financials (e.g. FED decisions), other sports (NBA, NFL). 

https://quantpedia.com/exploiting-mean-reversion-in-decentralized-prediction-markets-evidence-from-polymarket-binary-contracts/

While polymarket's overall Brier score of 0.0565 makes it one of the best predictive measures in existence, due to insider information and extensive advertising to keep losers in the game, when it comes to sports we observe a brier of 0.1899. Bookmaker's record Brier's of 0.1899-0.22. With PhD mathematicians constructing complex models, this leads me to believe polymarket odds aren't leading in this case. We can check the two way relationship between adjusted probabilities of bookies vs. polymarket odds. 

https://dune.com/alexmccullough/polymarket-brier-score

Markets to consider: US politics, esports, football, financials (e.g. FED decisions), other sports (NBA, NFL). 

We hypothesise potential mean-reversion relative to bookie's odds for sports/esports.

We focus on tournament/group-stage winners as we aren't trading single matches. We want reactions to "news" i.e. match results and then evaluate if there is a reverting period.This may lead to the question of momentum as well.

Volume of market is crucial, I expect: High volume market (e.g. NBA champion, go knicks!) have quick mean-reversion tendencies, low volume mmarkets have slower correction.

We must check the volume of markets too as time continues to evaluate how thin they are. As we will trade (if at all) very small amounts, no need to worry about slippage when moving a market. As we will trade the contract before resolution, the 2% fee isn't a worry. The major concern is the spread. On high volume markets the spread is typically 1-2¢. On thin markets it can be 3-5¢. Crucial to record spread as well to consider in calculation. We need sufficient volume for smooth price data.

Potential trading windows:
-NEVER during a match, highly volatile and I am not a HFT firm.
-First hour after a match, this is the potential overreaction period e.g. USA win a game and home fans splash the cash.
-Following 24-96 hours, or until next match (naturally if this is politics we won't know when the next market catalyst will occur so 24 hours up to a week seems sensible) will be mean reverting period.

Due to difficulty and costly retrieval of historical odds, this will be an analysis on the world cup vs. bookmakers. We will start from now to record the odds.

We will initially ignore the 2 cent spread. We also acknowledge this is low-frequency mean-reversion. We can go hours with no trades. Does this allow a patient orderinary trader to exploit mean reversion, especially as odds may converge towards resolution time?

Now we calculate the difference between polymarket probabilities and bookmaker adjusted probabilities. We care about the first differnce ACF. As the probabilities of the 2 sources diverge do they continue to diverge (polymarket momentum) OR do we see a negative ACF (mean-reverting tendencies). 
We also want to run a ADF test on the difference between the probabilities themselves to check if the difference is stationary. This would mean the markets are cointegrated and any diversion would support a mean-reverting trade.

HMM note: this could include a potential usage of a markov chain. 
2 potential regimes: spread is mean-reverting & spread is diverging

PROBLEM: Harder than originally anticipated to retrieve historical odds.

**06/06/2026**