py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
$env:GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
streamlit run app.py.venv\Scripts\activate.batpython3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install -r requirements.txt
export GEMINI_API_KEY="YOUR_GEMINI_API_KEY"
streamlit run app.py.venv/
__pycache__/
*.py[cod]
.env
.streamlit/secrets.toml
.DS_Storegit init
git add app.py requirements.txt README.md .gitignore
git commit -m "Build AI ATS Resume Checker"
git branch -M main
git remote add origin https://github.com/YOUR-USERNAME/YOUR-REPOSITORY.git
git push -u origin maingit config --global user.name "Your Name"
git config --global user.email "you@example.com"GEMINI_API_KEY = "YOUR_GEMINI_API_KEY"GEMINI_MODEL = "gemini-flash-latest"
