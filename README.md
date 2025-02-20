# Modeling Viewer Interactions and Watch Rates in Live Streams (Twitch)

This repository contains the analysis report for a project modeling viewer interactions and watch rates in live streams on Twitch. The project aims to understand the factors influencing user engagement and predict whether a user will watch a specific stream and estimate their watch time.

## Abstract

The 21st century has witnessed a transformative shift in media consumption, with traditional broadcasting evolving into dynamic and interactive platforms. Among these innovations is live streaming, a medium that gained traction in the early 2010s. Live streaming empowers creators—everyday individuals with a talent for entertainment—to build communities and engage audiences through diverse content such as music, sports watch-alongs, and, most notably, gaming. Gaming live streams, in particular, have cultivated passionate and tightly-knit communities, propelling the platform's rapid growth. Today, gaming-related live streaming platforms rank among the most visited websites globally, attracting over 240 million unique users monthly.

This phenomenon raises a critical question: how do these platforms successfully recommend such niche content to users? Are these recommendations driven by users' gaming preferences, affinities for certain streamers’ personalities, or patterns in their viewing behavior, such as schedules and consistency? To explore these questions, this project employs predictive modeling to analyze user-streamer interactions, addressing two fundamental challenges: predicting whether a user will watch a specific stream and estimating the duration of their engagement. By investigating these aspects, we aim to uncover the mechanisms behind personalized content delivery in live streaming, offering insights into user behavior and recommendation systems.

## Dataset

The dataset used in this project was collected by Jérémie Rappaz, Julian McAuley, and Karl Aberer for their paper "Recommendation on Live-Streaming Platforms: Dynamic Availability and Repeat Consumption" (2021).  It comprises anonymized identifiers for users, streams, and streamers, along with timestamps for interaction start and end times.  The data spans multiple days and captures diverse user and streamer interactions.  Key features engineered from this data include:

*   Relative time of day
*   Day of the week
*   Interaction durations
*   Gaps between interactions
*   Daily and weekly viewing patterns
*   Streamer popularity
*   User similarity (Jaccard similarity)
*   Stream similarity (Jaccard similarity)

The dataset did not explicitly contain "not watched" instances, but the abundance of observed interactions provided a robust foundation for analysis.

## Methodology

The project addresses two predictive tasks:

1.  **Will the User Watch a Stream?** (Binary Classification)
    *   Model: Logistic Regression (baseline), compared with Naive Bayes, Random Forests, and SVMs.
    *   Key Features: Streamer popularity, user similarity, stream similarity, user engagement patterns, temporal features (time of day, day of week), streamer availability.
    *   Evaluation Metrics: Accuracy, precision, recall, F1-score, AUC-ROC.

2.  **How Long Will the User Watch a Stream?** (Regression)
    *   Model: Temporal SVD++, compared with SVD++.
    *   Key Features: User watch history, streamer-specific trends, temporal features (time of day, day of week), user loyalty (interaction gaps).
    *   Evaluation Metrics: RMSE, MAE, R².

## Models Used

*   **Logistic Regression:**  Used for the binary classification task of predicting whether a user will watch a stream.
*   **Temporal SVD++:** A matrix factorization model used for predicting watch time, incorporating temporal dynamics.

## Results

*   **Interaction Prediction:** Logistic Regression and Random Forest performed best, with Logistic Regression preferred for its efficiency.
*   **Watchtime Prediction:** Temporal SVD++ achieved a reasonable RMSE, although the 10-minute timestamp conversion introduced some limitations.

## Conclusion

The project demonstrates the importance of temporal features, streamer popularity, and user interaction patterns in predicting user behavior on live streaming platforms.  While the models achieved reasonable performance, future work will explore additional features (content maturity, content type, game popularity, user sentiment) and refine the timestamp conversion for watchtime prediction to further improve accuracy.

## References

*   Rappaz, J., McAuley, J., & Aberer, K. (2021). Recommendation on live-streaming platforms: Dynamic availability and repeat consumption.
*   Koren, Y., Bell, R., & Volinsky, C. (2009). BellKor's Pragmatic Theory: User-based collaborative filtering with temporal dynamics. Proceedings of the Netflix Prize Workshop, 3-12.
