# Book Recommender System

Recommendation systems are becoming increasingly essential in our fast-paced world. With so much to do in just 24 hours, people often rely on recommendation systems to save time and make better decisions. Whether it’s choosing a book, movie, or song, these systems personalize recommendations to suit individual tastes and preferences.

This project focuses on building a **collaborative filtering-based book recommender system** using **Scikit-learn's KNeighbors algorithm** for unsupervised learning. The project also features a **Streamlit web application** that allows users to get personalized book recommendations based on their interests and ratings.

## Project Overview

This recommender system is built using collaborative filtering, which focuses on user-item interactions to make recommendations. The core idea is that users who have similar preferences will receive similar recommendations.

For this project, we’ve used the **KNeighbors algorithm** to identify the nearest neighbors of a user based on their book ratings. By analyzing the preferences of similar users, the model suggests books that a user might like.

### Key Features:
- **Collaborative Filtering:** Based on user-item interactions, the system clusters users with similar ratings and recommends books that similar users have enjoyed.
- **Streamlit Web Application:** Users can interact with the model and receive book recommendations directly through a user-friendly web interface.
- **Efficient Algorithm:** Using KNeighbors for finding similar users ensures that recommendations are generated quickly and effectively.

## Types of Recommendation Systems

This project focuses on collaborative filtering, but here’s a brief overview of common recommendation systems:

### 1. **Content-Based Filtering:**
   - Recommends items based on the characteristics of items and a user’s preferences.
   - Example: Recommending similar books based on the attributes (author, genre, etc.) of books a user has liked.

### 2. **Collaborative Filtering:**
   - Relies on past interactions between users and items to recommend new items.
   - Example: If User A and User B both liked Book X, and User B liked Book Y, then User A may also like Book Y.
   
### 3. **Hybrid Systems:**
   - Combines content-based and collaborative filtering techniques to improve recommendations by mitigating the shortcomings of each approach.

## Dataset

We used the [Books Recommendation Dataset](https://www.kaggle.com/ra4u12/bookrecommendation) from Kaggle, which includes user ratings for different books. The system identifies clusters of users with similar reading preferences and recommends books accordingly.

## Model

The model is built using **Scikit-learn's KNeighbors algorithm**, which is an unsupervised learning method. Here’s how the model works:

1. **Load the Data:** The dataset is loaded, and preprocessing is applied to clean and organize the data.
2. **Initialize K-Neighbors:** The number of neighbors (k) is initialized for the algorithm.
3. **Distance Calculation:** For each user, the algorithm calculates the Euclidean distance between that user and all other users based on their book ratings.
4. **Find Neighbors:** The algorithm sorts users based on the distance and identifies the top k neighbors.
5. **Generate Recommendations:** The model recommends books that the top k neighbors have rated highly but the user has not yet rated.
   
In this project, Pickle is used for serializing and saving the trained model and essential data objects into files. By using pickle.dump(), we can store the machine learning model (model.pkl), book names (book_names.pkl), final ratings (final_rating.pkl), and the book pivot table (book_pivot.pkl). These serialized files allow for easy loading and reuse of the model and data without needing to retrain or preprocess the dataset every time the application is run, improving efficiency and streamlining deployment.
## How to Run the Project

### Prerequisites

You will need the following tools to run the project:

- **Python 3.7.10 or later**
- **Conda (optional but recommended)**
- **Streamlit**
- **Scikit-learn**

### Steps to Run Locally:

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/cyrilbouharb/Book-Recommender.git
   ```

2. **Create a Conda Environment (Optional):**
   ```bash
   conda create -n books python=3.7.10 -y
   conda activate books
   ```

3. **Install Dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

4. **Run the Streamlit App:**
   ```bash
   streamlit run app.py
   ```

5. **Using the Application:**
   - First, click on "Train Recommender System" to generate the recommendation model.
   - Then, enter your book preferences and click "Show Recommendations" to see personalized book suggestions.

## Running the Project with Docker

You can also run the project using Docker if you prefer containerization:

1. **Build the Docker Image:**
   ```bash
   docker build -t streamlit .
   ```

2. **Run the Docker Container:**
   ```bash
   docker run -p 8501:8501 streamlit
   ```

3. **Access the App:**  
   Once the container is running, access the app by visiting `http://127.0.0.1:8501/`.
