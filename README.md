A beginner-friendly Streamlit app that uses Google's Gemini Flash model to estimate resume ATS readiness and suggest improvements.
Features
- Upload a resume as PDF, DOCX, or TXT (maximum 10 MB).
- Get an estimated ATS compatibility score out of 100.
- Optionally paste a job description for a separate job-match estimate.
- Review strengths, improvements, missing keywords, formatting issues, section feedback, and an action plan.
- See suggested rewrites for resume bullet points.
- Download the analysis as JSON.
- API key is entered at runtime or supplied through an environment variable / Streamlit secrets.
Important: This is an AI-generated estimate, not an official score from an employer's applicant tracking system. Never add a keyword, skill, achievement, or metric unless it is true. Text extraction may not work for image-only/scanned PDFs.

1. Create a Gemini API key
1. Open Google AI Studio.
2. Create or copy a Gemini API key.
3. Keep the key private. Never commit it to GitHub or place it directly in app.py.
The app defaults to gemini-flash-latest. If this model is not available for your API key, set GEMINI_MODEL to a supported Gemini Flash model listed in your Google AI Studio / Gemini API documentation.
2. Run locally
Install Python 3.10 or newer. Open a terminal in the project folder and run:
Windows (PowerShell)
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
$env:GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
streamlit run app.py
If PowerShell blocks activation, you can skip virtual-environment activation and use your normal Python environment, or activate the environment using Command Prompt:
.venv\Scripts\activate.bat
You can also paste the API key into the app's password field instead of setting GEMINI_API_KEY.
macOS / Linux
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
streamlit run app.py
Streamlit prints a local URL, usually http://localhost:8501.
3. Push the project to GitHub
Create a new, empty repository on GitHub. In your project folder, create a .gitignore file with:
.venv/
__pycache__/
*.py[cod]
.env
.streamlit/secrets.toml
.DS_Store
Then run these commands in the terminal, replacing the URL with your own repository URL:
git init
git add app.py requirements.txt README.md .gitignore
git commit -m "Build AI ATS Resume Checker"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin main
If Git asks you to configure your identity, use the name and email you want associated with your commits:
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
Do not commit your API key, .env file, or secrets.toml.
4. Deploy on Streamlit Community Cloud
1. Push the three project files and .gitignore to GitHub.
2. Open Streamlit Community Cloud and sign in with GitHub.
3. Select Create app (or Deploy an app).
4. Choose your repository, branch (main), and main file path (app.py).
5. Deploy the app.
6. Open the deployed app's Settings → Secrets and add:
GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"
7. Save the secret and reboot/redeploy the app if needed.
The app reads GEMINI_API_KEY from the environment, so you do not need to expose it in the source code. If you need to change the model, you can also add a secret such as:
GEMINI_MODEL = "gemini-flash-latest"
The default model can be changed in the app's environment/secrets if the model name is not available to your API key.
5. Troubleshooting
- Invalid API key: Create/check the key in Google AI Studio and update the local environment or Streamlit secrets.
- Model not found / 404: Check which Gemini Flash model names are currently available to your key. Set GEMINI_MODEL to one of those exact names.
- Quota / 429: Check your Gemini API quota and billing/usage limits.
- No text found: The resume may be a scanned/image-only PDF. Use a text-based PDF or DOCX.
- Missing Python package: Activate your virtual environment and run pip install -r requirements.txt again.
- Changes do not appear online: Commit and push your changes, then check the Streamlit app's deployment logs.
Privacy note
Resume files and their extracted text are sent to the Gemini API for analysis. Do not upload a resume unless you have permission to process its personal information. This sample app does not intentionally save uploaded files to a database, but API provider policies and deployment logs may apply.
