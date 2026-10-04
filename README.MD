# 🧾 BillSplit

Snap a photo of a restaurant bill or receipt, tell the AI how many people are sharing, and get an instant split. One button emails the full breakdown to your inbox.

**Live app:** https://billsplit-b5btmkczmbwwkffmzszqz4.streamlit.app

## What it does

- Enter your name and email once.
- Chat with an AI bill-splitting assistant: attach a photo of a bill, or type a question.
- It reads every item, the taxes and the total, and flags numbers it can't read or that don't add up.
- Split the bill equally, by item, or with a tip. Currency is kept as printed on the bill.
- Click **Email me the split** to get a plain-text summary by email.

## Built with

- Streamlit for the chat interface
- Google Gemini for chat and reading bill photos
- Gmail SMTP (Python's built-in `smtplib`) for sending the summary

## Project structure

```
BillSplit/
├── app.py                      # the app itself
├── prompts.py                  # the AI's instructions and email prompt
├── requirements.txt            # dependencies
├── .gitignore                  # keeps secrets.toml out of GitHub
└── .streamlit/
    └── secrets.toml.example    # template for your keys
```

## Run locally

1. Install Python 3.9 or newer.
2. Create and activate a virtual environment:

```
   python -m venv venv
   .\venv\Scripts\Activate.ps1      # Windows PowerShell
   source venv/bin/activate         # macOS / Linux
```

3. Install dependencies:

```
   python -m pip install -r requirements.txt
```

4. Get a Gemini API key from [Google AI Studio](https://aistudio.google.com).
5. On the Gmail account that will send the emails, turn on 2-Step Verification, then create an App Password at [myaccount.google.com/apppasswords](https://myaccount.google.com/apppasswords).
6. Copy `.streamlit/secrets.toml.example` to `.streamlit/secrets.toml` and fill in:
   - `GEMINI_API_KEY`
   - `GMAIL_ADDRESS`
   - `GMAIL_APP_PASSWORD`
7. Run the app:

```
   python -m streamlit run app.py
```

It opens at http://localhost:8501.

## Deploy

Push the project to GitHub (never commit `secrets.toml`), create an app on [share.streamlit.io](https://share.streamlit.io) pointing at `app.py`, and paste the same three secrets into **Advanced settings → Secrets**.

## Notes

- The free Gemini tier has a daily request limit, so the app may pause until the quota resets.
- Gemini can misread a blurry photo. The assistant is told to flag unclear numbers instead of guessing, but always check the totals.
