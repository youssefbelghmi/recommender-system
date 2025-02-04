# Book Recommendation Systems

## Project Overview

This project aims to build a book recommendation system that predicts user ratings based on a dataset of over 16,000 books. Different recommendation techniques were applied and assessed to enhance accuracy. The objective was to explore and compare various approaches, identifying their advantages and drawbacks while ensuring both performance and efficiency.

## Methods

### 1. Collaborative Filtering
Collaborative filtering predicts user preferences based on past interactions between users and books. Two approaches were implemented:

- **User-Based Collaborative Filtering**: Finds similar users and predicts a rating based on their past ratings.
- **Item-Based Collaborative Filtering**: Computes similarities between books and predicts ratings based on user preferences for similar books.

Results:
- User-Based Collaborative Filtering RMSE: 1.01336
- Item-Based Collaborative Filtering RMSE: 0.87414

### 2. Content-Based Recommendation
This method recommends books by analyzing their metadata, including descriptions and themes retrieved from external APIs. The model used **sentence embeddings** to compute book similarities.

Results:
- Content-Based Recommendation RMSE: 0.82904

### 3. Matrix Factorization (SVD-Like Approach)
Matrix factorization decomposes the user-book interaction matrix into latent factors representing user preferences and item characteristics. Bias terms were incorporated to improve prediction accuracy. A **grid search** was performed to tune hyperparameters such as latent dimensions, learning rate, and regularization.

Results:
- Matrix Factorization RMSE: 0.79190 (best performance)

## Evaluation and Results

Each method was evaluated using **Root Mean Square Error (RMSE)** to measure prediction accuracy. Matrix factorization achieved the best results and was selected for the final **Kaggle submission** due to its ability to capture hidden patterns in user-book interactions.

## Conclusion

This project demonstrates the advantages and limitations of different recommendation techniques:
- **Collaborative filtering** provides personalized recommendations but struggles with sparse data.
- **Content-based methods** leverage book metadata effectively but depend on the completeness of the available information.
- **Matrix factorization** balances accuracy and computational efficiency, making it the most effective approach for this dataset.

Future work could explore **hybrid approaches**, combining collaborative and content-based methods to mitigate weaknesses such as the cold-start problem for new users and books.

## Authors

This work was carried out by Youssef Belghmi, Hamza Morchid, and Amine Belghmi, Master Data Science students at EPFL, as part of the Distributed Information Systems (CS-423) course project.
