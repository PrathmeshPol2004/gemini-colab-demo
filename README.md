# Gemini Colab Demo

This project shows how to use **Google Gemini API** in Colab.  
You can read PDF files and work with data using **Pandas**.


## What it does

- Use **Google Gemini API** safely.
- Read text from PDF files with **pdfplumber**.
- Work with data using **Pandas**.
- Keep your API key secret.


## Files

gemini-colab-demo/
│
├── notebooks/
│   └── Gemini\_PDF\_Demo.ipynb   # Main Colab notebook
├── data/
│   └── sample.pdf              # Example PDF
├── requirements.txt            # Python packages
├── README.md                   # This file
└── .gitignore                  # Ignore secret files


## How to use

1. Clone the repo:

```bash
git clone https://github.com/YOUR_USERNAME/gemini-colab-demo.git
cd gemini-colab-demo
````

2. Install packages:

```bash
pip install -r requirements.txt
```

3. Add your Gemini API key in Colab:

* Go to **Tools > Settings > Secrets**.

* Add a secret:

  * Name: `GEMINI_KEY`
  * Value: `<YOUR_GEMINI_API_KEY>`

* Use it in notebook:

```python
from google.colab import userdata
import google.generativeai as genai

gemini_api_key = userdata.get('GEMINI_KEY')
genai.configure(api_key=gemini_api_key)
```

4. Open `notebooks/Gemini_PDF_Demo.ipynb` in Colab.
5. Upload PDFs to `data/` folder (optional).
6. Run the notebook.

## Security

* Do **not** put your API key in the code.
* `.gitignore` ignores secret files.
* Colab Secrets keeps your key safe.


## Example

```python
from google.colab import userdata
import google.generativeai as genai
import pdfplumber
import pandas as pd

gemini_api_key = userdata.get('GEMINI_KEY')
genai.configure(api_key=gemini_api_key)

# Read PDF
with pdfplumber.open("data/sample.pdf") as pdf:
    text = "\n".join([page.extract_text() for page in pdf.pages])

# Summarize text
response = genai.generate_text(prompt=f"Summarize this:\n{text}")
print(response.text)
```

## License

MIT License – see LICENSE file.

```


✅ **This is fully copy-paste ready.**  
No complex words, easy for beginners, and it explains exactly what to do.  

If you want, I can **also make a matching ready-to-use Colab notebook** so your repo is fully demo-ready.  

Do you want me to do that?
```
