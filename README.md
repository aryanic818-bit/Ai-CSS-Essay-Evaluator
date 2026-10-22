# Ai-CSS-Essay-Evaluator# 📝 CSS Essay Evaluator

Paste or upload an essay written for the CSS exam and get:

- a **score out of 20** (Structure, Grammar, Arguments and Vocabulary, each out of 5)
- detailed **feedback** on each of the four areas, with strengths and how to improve
- the **top 3 priorities** to fix first
- real **grammar corrections** quoted from your essay
- a rewritten, **improved introduction**
- a downloadable Markdown report

Built with [Streamlit](https://streamlit.io) and Google's Gemini Flash model (`gemini-3.5-flash`).
If the model is busy, the app retries automatically and switches to a backup Flash model.

> The score is an AI estimate for practice. It is not an official examiner's mark.

## Files

| File | Purpose |
|------|---------|
| `app.py` | The Streamlit app |
| `requirements.txt` | Python dependencies |
| `README.md` | This guide |

## Run locally

1. Install Python 3.9+ and get a free API key from [Google AI Studio](https://aistudio.google.com/app/apikey).
2. Install the dependencies:
   ```bash
   pip install -r requirements.txt
   ```
3. Set your key (or paste it into the app's sidebar):
   - Mac/Linux: `export GEMINI_API_KEY="your-key"`
   - Windows (PowerShell): `$env:GEMINI_API_KEY="your-key"`
4. Start the app:
   ```bash
   streamlit run app.py
   ```

## Put it on GitHub

1. Create a free account at [github.com](https://github.com) and click **New repository** (for example `css-essay-evaluator`, set to **Public**; do not add any files).
2. Create a `.gitignore` file in your project folder with these lines, so your key is never uploaded:
   ```
   .streamlit/secrets.toml
   __pycache__/
   ```
3. In your project folder, run:
   ```bash
   git init
   git add app.py requirements.txt README.md .gitignore
   git commit -m "Initial commit"
   git branch -M main
   git remote add origin https://github.com/YOUR-USERNAME/css-essay-evaluator.git
   git push -u origin main
   ```
   (No Git? On GitHub choose **Add file → Upload files** and drag the files in.)

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
2. Click **Create app**, choose your repository, branch `main`, and main file `app.py`.
3. Open **Advanced settings → Secrets** and paste:
   ```toml
   GEMINI_API_KEY = "your-key"
   ```
4. Click **Deploy**. In a minute or two you get a public link to share.

## Notes and limits

- Supported files: PDF (text-based, not scans), DOCX and TXT. Handwritten or scanned essays cannot be read.
- Essays need at least 100 words. Very long essays are cut to the first 30,000 characters (about 5,000 words).
- The optional topic field helps the examiner judge how relevant your arguments are.
- Use the improved introduction as a model, then rewrite it in your own words.
- You can change the model name in the sidebar if Google releases a newer Flash model.
