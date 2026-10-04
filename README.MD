# BillSplit

Snap a photo of a receipt or bill. AI reads the items and total, splits it
by person, and emails you the breakdown.

Built with Streamlit and Gemini.

## Run locally

1.  Create a virtual environment: `python -m venv venv`
2.  Activate it: `.\venv\Scripts\Activate.ps1` (Windows)
3.  Install dependencies: `pip install -r requirements.txt`
4.  Copy `.streamlit/secrets.toml.example` to `.streamlit/secrets.toml`
    and fill in your keys.
5.  Run: `python -m streamlit run app.py`
