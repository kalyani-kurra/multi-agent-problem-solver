# Multi-Agent Real-World Problem Solver

## Important scope note
This starter project implements a multi-agent workflow based on the uploaded Generative AI guide: Planner Agent → Solution Agent → Reviewer Agent. The uploaded file appears to be a conceptual Generative AI guide, not a specific Multi-Agent Project Requirement Document. Replace the example problem with the exact lecturer-provided problem and requirements when available.

## Features
- Three distinct agent roles, each called separately
- User-provided problem and context
- Reviewer pass to identify gaps and risks
- Streamlit web interface
- Downloadable Markdown report
- API key entered at runtime or stored in Streamlit Secrets
- No key hard-coded in source

## Run locally (fastest: VS Code)
1. Install Python 3.11 or 3.12 if possible.
2. Extract this ZIP and open the `multi_agent_project` folder in VS Code.
3. Open Terminal in that folder.
4. Create and activate a virtual environment:

   Windows:
   ```powershell
   py -3.11 -m venv .venv
   .venv\Scripts\activate
   ```

   If `py -3.11` is unavailable, use `python -m venv .venv` with an installed supported Python version.

5. Install dependencies:
   ```bash
   python -m pip install --upgrade pip
   pip install -r requirements.txt
   ```
6. Start the app:
   ```bash
   streamlit run app.py
   ```
7. In the browser, enter a problem, paste requirements/context, enter your Google Gemini API key in the sidebar, and run the agents.

## Get an API key
Create a Gemini API key in Google AI Studio. Keep it private. Do not paste it into `app.py`, commit it to GitHub, or include it in screenshots. Provider quotas and model availability may vary.

## Deploy to Streamlit Community Cloud
1. Create a GitHub repository, for example `multi-agent-problem-solver`.
2. Upload `app.py`, `requirements.txt`, and `README.md` to the repository. Do not upload `.venv`, API keys, or `.streamlit/secrets.toml`.
3. Sign in to Streamlit Community Cloud and create a new app from that repository.
4. Set the main file path to `app.py`.
5. In the app's Settings / Secrets section, add:
   ```toml
   GOOGLE_API_KEY = "YOUR_REAL_KEY_HERE"
   ```
   Replace the placeholder with your key. Do not commit this secrets entry to GitHub.
6. Deploy and wait for the build to finish. Open the app URL and test it with a simple problem.
7. Share the deployed URL with your lecturer. Confirm the lecturer can access it; never share the API key.

## Suggested demo problem
"A college receives repeated student questions about course topics and project requirements. Design a workflow that helps students receive clear, structured guidance."

This is only a demo example, not a claim about the missing lecturer PRD.

## What to explain to the lecturer
- Multi-agent design: each agent has a separate role and prompt.
- Orchestration: the Python application calls agents in a fixed sequence and passes earlier outputs to later agents.
- Review: the Reviewer Agent checks for gaps and produces an improved final response.
- UI: Streamlit provides the form, progress status, tabs, and report download.
- Security: API key is supplied through runtime input or deployment secrets.
- Limitations: agents are separate LLM calls, not independent deployed services; no web browsing or external tools are enabled; model output needs human review.

## Troubleshooting
- `ModuleNotFoundError`: activate the virtual environment and run `pip install -r requirements.txt`.
- API key error: confirm the key is valid and has quota; restart the app after changing secrets.
- Model not found: check current model availability for your API key, then update the model name in the sidebar.
- Slow responses / quota error: retry later or use a model available under your account.
- Deployment build error: confirm `app.py` and `requirements.txt` are at the repository root.
