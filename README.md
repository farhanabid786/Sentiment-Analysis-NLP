# ML_DL_NLP_Projects

This repository contains a collection of machine learning, deep learning, and NLP projects built for experimentation and practical learning. The main application in this repo is an NLP sentiment analysis web app that classifies user-entered review text through a Flask interface.

## Overview

The sentiment analysis project demonstrates a typical end-to-end NLP workflow:

1. Collect or provide review text as input.
2. Clean and normalize the text.
3. Convert the text into TF-IDF features.
4. Load a trained machine learning model.
5. Predict the sentiment class and show the result in the browser.

The app is designed to be simple to run locally and easy to extend if you want to experiment with new models, datasets, or UI improvements.

## NLP Sentiment Analysis Project

The sentiment analysis app lives in `sentiment-classifier-nlp/`. It combines NLTK-based preprocessing, TF-IDF vectorization, and a trained scikit-learn model to predict the sentiment of user-entered text.

### Key Features

- Takes a short review or sentence from a web form
- Removes non-letter characters and normalizes the text
- Applies tokenization, stop-word removal, and lemmatization
- Uses a saved TF-IDF vectorizer for feature extraction
- Predicts one of the supported sentiment labels: positive, negative, neutral, or irrelevant
- Displays the prediction result directly in the HTML template

### How It Works

The Flask app in `sentiment-classifier-nlp/app.py` handles the prediction flow. When a user submits text from the homepage, the app preprocesses the input using NLTK, loads the vectorizer stored in `cv.pickle`, transforms the text into a numerical representation, and then feeds the transformed vector into `nlp_review_sentiment_model.pkl`.

The current interface is intentionally lightweight so the focus stays on the NLP pipeline rather than a complex front end. That also makes it easier to test ideas quickly in notebooks and then plug the model into the Flask app.

## Project Structure

- `sentiment-classifier-nlp/app.py` - Flask application and prediction endpoint
- `sentiment-classifier-nlp/templates/index.html` - Front-end form for submitting text
- `sentiment-classifier-nlp/cv.pickle` - Saved TF-IDF vectorizer
- `sentiment-classifier-nlp/nlp_review_sentiment_model.pkl` - Trained sentiment model
- `sentiment-classifier-nlp/twitter_training.csv` - Training data used for the NLP project
- `sentiment-classifier-nlp/NLP_review_sentiment.ipynb` - Notebook used for experimentation and model development
- `FakeNewsClassifier.ipynb` - Separate notebook for fake news classification experiments
- `SpamClassifierNLP.ipynb` - Separate notebook for spam classification experiments
- `SMSSpamCollection` - Dataset used for spam-related NLP work

## Setup

Create a virtual environment and install the dependencies listed in `sentiment-classifier-nlp/requirements.txt.txt`.

```bash
cd sentiment-classifier-nlp
pip install -r requirements.txt.txt
```

If you are working in a fresh environment, make sure the required NLTK resources can be downloaded when the app starts.

## Run the App

Start the Flask application from the project folder:

```bash
python app.py
```

By default, Flask will start a local development server. Open the shown local address in your browser, enter a review, and click **Predict** to see the sentiment result.

## Working With the Project

- Update the notebook in `sentiment-classifier-nlp/NLP_review_sentiment.ipynb` if you want to retrain or compare models.
- Keep the saved model and vectorizer files in the same folder as `app.py`, because the app loads them directly at runtime.
- Use the `templates/index.html` file if you want to change the web form or improve the output presentation.
- Replace the training data if you want to experiment with a different domain or sentiment dataset.

## Notes

- The app downloads the required NLTK resources on startup: `stopwords`, `wordnet`, and `omw-1.4`.
- The model expects the vectorizer and trained `.pkl` files to remain in the `sentiment-classifier-nlp/` directory.
- This repository also includes other NLP notebooks and datasets for experimentation, such as spam and fake news classification.

## Contributing

This project is open to make changes. If you want to improve the model, refine the UI, add new NLP projects, or fix documentation, feel free to open an issue or submit a pull request.

## Author

Farhan Abid
