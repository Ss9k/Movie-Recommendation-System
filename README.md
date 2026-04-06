*How It Works*

This system uses Content-Based Filtering — it recommends movies by analyzing what a movie is about, not what other users watched.
Here's the pipeline:

Data Preprocessing — Load and clean TMDB movie metadata. Extract genres, keywords, top 3 cast members, and the director into a unified tags column per movie.
Vectorization — Convert the tags into numerical vectors using Bag of Words (CountVectorizer).
Stemming — Apply stemming via NLTK to reduce words to their root form (e.g. "loving" → "love"), improving matching accuracy.
Cosine Similarity — Compute similarity scores between all movie vectors. Cosine similarity is used over Euclidean distance because it performs better in high-dimensional space.
Recommendation — When you pick a movie, the system fetches the top 5 most similar movies and displays them with posters pulled from the TMDB API.


Demo

<img width="1310" height="802" alt="ss 1" src="https://github.com/user-attachments/assets/d51d0043-d04d-4eac-ad59-25fcbcd86461" />
<img width="1533" height="847" alt="ss2" src="https://github.com/user-attachments/assets/f3917935-51f6-4d06-9593-fb19640e266c" />

📁 Project Structure
movie-recommender-system/
│
├── app.py                  # Streamlit frontend
├── movie_recommender.ipynb # Data processing & model building notebook
├── tmdb_5000_movies.csv    # Raw dataset (movies) (downloaded from kaggle)
├── tmdb_5000_credits.csv   # Raw dataset (credits)
├── requirements.txt        # Dependencies
└── README.md

Note: similarity.pkl and movies.pkl are not included in this repo due to their large file size. Generate them by running the notebook (see Setup below).


⚙️ Setup & Installation
1. Clone the repository
bashgit clone https://github.com/Ss9k/movie-recommendation-system.git
cd movie-recommender-system
2. Install dependencies
bashpip install -r requirements.txt
3. Download the dataset
Download the TMDB 5000 Movie Dataset from Kaggle and place both CSV files in the root directory.
4. Generate the model files
Open and run all cells in movie_recommender.ipynb. This will create:

movies.pkl — processed movie dataframe
similarity.pkl — precomputed cosine similarity matrix

5. Get a TMDB API key

Sign up at themoviedb.org
Go to Settings → API → Request an API key
Replace the placeholder in app.py:

6. Run the app
bashstreamlit run app.py

🛠️ Tech Stack
ToolPurposePythonCore languagePandasData loading & cleaningscikit-learnCountVectorizer, cosine similarityNLTKStemmingStreamlitWeb app frontendTMDB APIFetching movie posters

📊 Dataset
TMDB 5000 Movie Dataset from Kaggle — contains metadata for 5000 movies including genres, cast, crew, keywords, and more.
