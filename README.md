# Breast-cancer-Detection
🧬 Cancer Prediction Flask App This project is a simple web application built using Flask and Jinja2 templating. It allows users to input medical feature values and predicts whether the case is cancerous or not cancerous using a pre-trained machine learning model.

# 🧠 Breast Cancer Detection Web App

This is a machine learning web application built with **Flask** that predicts whether a tumor is **cancerous** or **not cancerous** based on user-input features. It uses a trained classification model (e.g., Logistic Regression or Random Forest) to process numerical features and returns a prediction in real time through a web interface.

---

## 📌 Features

- User-friendly HTML interface (via Jinja templating)
- Takes comma-separated numerical features as input
- Displays prediction: "Cancerous" or "Not Cancerous"
- Powered by a pre-trained ML model
- Deployed locally using Flask

---

## 🚀 Tech Stack

- Python 🐍  
- Flask 🌐  
- NumPy  
- Jinja2 (HTML templating)  

---

## 🖼️ Web Interface

The user inputs features (e.g., mean radius, texture, etc.) as a comma-separated string. Upon submission, the Flask backend:
1. Parses the input
2. Converts it into a NumPy array
3. Uses the loaded ML model to predict
4. Displays the result using Jinja templating in `index.html`

---

## 🧪 Sample Code

```python
@app.route("/")
def index():
    return render_template("index.html")

@app.route("/predict", methods=["POST"])
def predict():
    features = request.form["feature"]
    features_lst = features.split(",")
    np_features = np.asarray(features_lst, dtype=np.float32)
    pred = model.predict(np_features.reshape(1, -1))
    output = ["Cancerous" if pred[0] == 1 else "Not Cancerous"]
    return render_template("index.html", message=output)
