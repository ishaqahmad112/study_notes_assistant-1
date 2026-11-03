# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.# 📚 Study Notes Assistant

A Streamlit app that turns your notes into study material using Google's **Gemini Flash** models.

## Features

- **Paste text or upload** a `.txt`, `.md` or `.pdf` file
- **Summary** in three lengths (short / medium / detailed), downloadable as Markdown
- **Key points**: a structured outline plus a glossary of key terms
- **Flashcards**: expandable cards, exportable as CSV for Anki or Quizlet
- **Practice quiz**: multiple-choice with scoring and explanations
- **Ask questions**: chat with your notes
- Choose the explanation level (middle school to professional) and the Gemini model

## Project files

```
app.py            the Streamlit app
requirements.txt  Python dependencies
README.md         this file
```

## Run locally

1. Install Python 3.10 or newer.
2. Get a free API key from [Google AI Studio](https://aistudio.google.com/apikey).
3. In a terminal, inside the project folder:

```bash
python -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
streamlit run app.py
```

4. Your browser opens at `http://localhost:8501`. Paste your API key in the sidebar.

**Optional:** to avoid pasting the key every time, create `.streamlit/secrets.toml`:

```toml
GEMINI_API_KEY = "your-key-here"
```

or set an environment variable named `GEMINI_API_KEY`.
Never upload `secrets.toml` to GitHub.

## Choosing a model

The sidebar lists several Flash models, and the first (`gemini-3.8-flash`) is the default.
Google releases and retires models often, so if you see a "model not found" message,
check the current list at <https://ai.google.dev/gemini-api/docs/models> and type
the model ID into **Custom model ID** (no code change needed).
To change the default, edit `MODEL_OPTIONS` at the top of `app.py`.

## Push the project to GitHub (using the website)

1. Sign in at [github.com](https://github.com) (create a free account if needed).
2. Click the **+** icon (top right) then **New repository**.
3. Enter a name such as `study-notes-assistant`, choose **Public**, and leave
   "Add a README file" **unchecked** (you already have one). Click **Create repository**.
4. On the empty repository page, click **uploading an existing file**.
5. Drag `app.py`, `requirements.txt` and `README.md` into the page.
   Upload only these files, never your API key or `secrets.toml`.
6. Type a commit message such as `Initial commit` and click **Commit changes**.

To update later: open a file in the repository, click the pencil icon (Edit), change it, and commit.
Streamlit Cloud redeploys automatically after each commit.

## Deploy on Streamlit Community Cloud

1. Go to [share.streamlit.io](https://share.streamlit.io) and sign in with GitHub.
   Allow access to your repository when asked.
2. Click **Create app** and choose to deploy from an existing GitHub repository.
3. Select your repository, the `main` branch, and set **Main file path** to `app.py`.
4. Open **Advanced settings**, find **Secrets**, and paste:

```toml
GEMINI_API_KEY = "your-key-here"
```

5. Click **Deploy**. The first build takes a minute or two while dependencies install.
   You get a public URL like `https://your-app-name.streamlit.app`.

> **Important:** if you store your key in Secrets, anyone with the link can use your quota.
> To avoid that, leave the secret out so visitors enter their own key in the sidebar,
> or set the app to private in the Streamlit Cloud sharing settings.

## Troubleshooting

| Problem | Fix |
|---|---|
| "Gemini rejected the API key" | Re-copy the key from AI Studio; make sure there are no spaces. |
| "Rate limit or quota reached" | The free tier has per-minute and per-day limits. Wait, or switch models. |
| "Model ID was not found" | Pick another model in the sidebar or enter a current ID in **Custom model ID**. |
| "No text could be read" from a PDF | The PDF is probably scanned images. Use a text-based PDF or paste the text. |
| Import errors on deploy | Make sure `requirements.txt` is in the repository root, then reboot the app. |
| SDK errors after an update | Run `pip install -U google-genai` locally, or reboot the app on Streamlit Cloud. |

## Notes

- Very long notes are trimmed to about 80,000 characters.
- Flashcards and quizzes come from AI output, so double-check anything important against your source material.
- Notes you submit are sent to the Gemini API. Do not paste confidential material.
