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

First data-set will be the "Ballon d'or winner 2026". It is a long-running Polymarket contract with continuous price updates reacting to discrete performance events. We can check responses to Harry Kane vs. Dembele. 

- *Claude event summary:*
    Market Overview
    The 2026 Ballon d'Or Polymarket contract is a long-running multi-candidate market resolving October 2026. Current standings post-UCL final: Dembele 52%, Kvaratskhelia 50%, Kane 27%. Bet365 has Kane at 2/1 favourite — notable cross-market divergence already present before the World Cup begins.
    This market is ideal as a pilot dataset because it contains multiple discrete information shocks across a defined window (May 6 – May 30), two main candidates whose prices move inversely, and a clean resolution date. Historical price data is pullable via the Polymarket data API for the full season.

    Kane — Last 4 Matches
    6 May, UCL Semi-Final Leg 2 — Bayern 1–1 PSG (PSG win 6-5 on aggregate). Kane scored but Bayern were eliminated. Primary negative shock for his Ballon d'Or odds.
    9 May, Bundesliga — Wolfsburg 0–1 Bayern. Kane scored. Routine win, minor positive.
    16 May, Bundesliga final day — Bayern 5–1 Köln. Bundesliga title confirmed. Positive shock — third consecutive Bundesliga Golden Boot with 36 goals, top scorer.
    23 May, DFB-Pokal Final — Bayern 3–0 VfB Stuttgart. Kane hat-trick. Primary positive shock — domestic double confirmed, 61 goals in 51 games across the full season.

    Dembele — Last 4 Matches
    10 May, Ligue 1 — PSG 1–0 Brest. Dembele scored — his 8th consecutive game on the scoresheet, matching a PSG record previously held by Neymar and Mbappe. Minor positive.
    13 May, Ligue 1 — Lens 0–2 PSG. Dembele scored. Routine win, minor positive.
    17 May, Coupe de France — Paris FC 2–1 PSG. Dembele did not score. Cup elimination — minor negative shock.
    30 May, UCL Final — PSG 1–1 Arsenal, PSG win 4-3 on penalties. Dembele scored the penalty equaliser in the 65th minute. PSG become back-to-back Champions League winners. Primary positive shock — largest single event in this window. Bookmakers moved Dembele from 20/1 in late April to 7/2 following this result.

    Three Events To Test
    May 6 — Kane eliminated from UCL. Kane odds should drop, Dembele odds should rise simultaneously. Did Polymarket overshoot on both? What was the magnitude relative to a rational update and how long until prices stabilised?
    May 23 — Kane hat-trick in DFB-Pokal Final. Kane odds should recover. Key question: did the May 6 drop over-correct, making this recovery a mean reversion trade rather than purely new information? If Kane was already below fair value post-May 6, the hat-trick accelerates reversion rather than causing a fresh positive shock.
    May 30 — UCL Final, Dembele goal and PSG title. Largest event. Dembele should surge. Was the Polymarket move proportionate and immediate or gradual? Bookmakers repriced dramatically — does Polymarket lead, lag, or match that move?

We will initially ignore the 2 cent spread. We also acknowledge this is low-frequency mean-reversion. We can go hours with no trades. Does this allow a patient orderinary trader to exploit mean reversion, especially as odds may converge towards resolution time?

