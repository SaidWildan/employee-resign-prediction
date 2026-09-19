# Employee Resign Prediction

A small machine learning web app that predicts whether an employee is likely to resign, based on a few HR attributes. Built as the final deployment project of the **AI for Jobs (Kampus Merdeka / Orbit Future Academy) Batch 3** program in 2022.

## How it works

The user fills in a form in the browser. The Flask backend scales the input with a pre-fitted scaler, runs it through a trained scikit-learn classifier, and shows the result (**Akan Resign** / **Tidak Resign**) together with the model's confidence score.

### Input features

| Field | Description |
|---|---|
| Lama Bekerja | Years at the company |
| Jam Kerja Perbulan | Average working hours per month |
| Kecelakaan Kerja | Has had a work accident (yes / no) |
| Kategori Gaji | Salary category: Low, Middle, High |
| Tingkat Kepuasan | Job satisfaction level (0 to 100) |

## Tech stack

Python, Flask, scikit-learn, pickle (model serialization), HTML + Bootstrap 5.

## Project structure

```
app.py              Flask routes (form page and /predict)
model.py            Loads the model and scaler, runs the prediction
model/              Trained model and scaler (.pkl)
templates/index.html  Web form and result view
static/image/       Logos
```

## Running locally

```bash
git clone https://github.com/SaidWildan/employee-resign-prediction.git
cd employee-resign-prediction
pip install flask scikit-learn
python app.py
```

Then open http://127.0.0.1:5000 in your browser.

> The model was trained in 2022 (Python 3.9). If loading the .pkl files shows a version warning or error, install a scikit-learn version close to the one used at training time.

## Security note

The original version ran with `debug=True` on `0.0.0.0`, which exposes the Werkzeug interactive debugger to the network and can allow remote code execution. The app now runs with debug mode off and binds to localhost only. For any real deployment, use a production WSGI server (for example gunicorn) behind a reverse proxy instead of the Flask development server.

## Author

Said Muhammad Wildan
