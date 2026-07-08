# Factify AI

A web interface for detecting fake news using a hybrid Machine Learning + LLM system. Paste text, upload files (including PDFs), or check news content and get a Real/Fake verdict with a confidence score and explanation.

## Screenshots
<img width="627" height="505" alt="image" src="https://github.com/user-attachments/assets/0234815a-2509-41f5-9858-a14f7d221469" />
<img width="638" height="318" alt="image" src="https://github.com/user-attachments/assets/f0df88fb-8a1e-4d1f-84e5-a9c3c2a6c1cd" />
<img width="846" height="528" alt="image" src="https://github.com/user-attachments/assets/2b1672a9-88ea-4a32-932e-5ed89ff3f03e" />
<img width="948" height="394" alt="image" src="https://github.com/user-attachments/assets/b30449c9-7748-408d-8704-590ae4aa8c6a" />
<img width="935" height="400" alt="image" src="https://github.com/user-attachments/assets/8440f6d4-764d-4286-8157-c8e4fb7de420" />
<img width="950" height="407" alt="image" src="https://github.com/user-attachments/assets/6ba5a2bd-39cb-4316-b3bc-48628f7aeef2" />


## Features

- Paste text or upload a file (.pdf or .txt) to check for fake news
- Hybrid backend: ML ensemble (Logistic Regression, Decision Tree, Random Forest, Gradient Boosting) with an LLM fallback (Groq) for low-confidence cases
- Returns verdict, confidence score, and a short reason
- Simple, clean UI — Home, How It Works, Check News, About

## Tech Stack

- **Frontend:** HTML, CSS, JS
- **Backend:** Flask (Python)
- **Deployment (dev/demo):** Google Colab + ngrok tunnel
- **Model:** scikit-learn ensemble + Groq LLM fallback

## Results

<img width="889" height="590" alt="image" src="https://github.com/user-attachments/assets/de032a62-71fd-4db9-981e-9e1fa5720acd" />
                        Model  Accuracy  Precision    Recall        F1
0  Hybrid (ML + LLM fallback)  0.884000   0.891304  0.897810  0.894545
1               Random Forest  0.879790   0.870255  0.924404  0.896513
2         Logistic Regression  0.860356   0.853627  0.907734  0.879850
3               Decision Tree  0.850311   0.868482  0.865284  0.866880
4           Gradient Boosting  0.832951   0.791486  0.955030  0.865601

## Dataset

This project was trained on a combination of the following publicly available datasets:

- [LIAR](https://www.cs.ucsb.edu/~william/data/liar_dataset.zip) — political statement fact-checking dataset
- [FakeNewsNet](https://github.com/KaiDMML/FakeNewsNet) — GossipCop and PolitiFact sources
- [Fake and Real News Dataset](https://www.kaggle.com/datasets/clmentbisaillon/fake-and-real-news-dataset) — Kaggle
- [Constraint@AAAI2021 COVID-19 Fake News Dataset](https://constraint-shared-task-2021.github.io/) — short-form claims/tweets

See the [Fake News Detection](link-to-your-training-repo) repo for the full data pipeline, model training, and evaluation.

## Running Locally

```bash
git clone https://github.com/<your-username>/factify-ai.git
cd factify-ai
pip install flask pyngrok
python app.py
```

*(Currently runs via ngrok for demo purposes — replace with a standard deployment for production use.)*

## Author

Built by Isha, supervised by Dr. Umair Muneer.
