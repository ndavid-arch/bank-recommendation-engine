## Lesson 1 – Setup & first look at the data (5 Oct 2026)
**Did:** set up venv, installed libraries, loaded UCI Bank Marketing data
**Learned:** features (X) vs target (y), class imbalance (11.7% yes), data leakage (`duration`)
**Problems & fixes:**
- Git Bash needs `source .venv/Scripts/activate` (forward slashes)
- Connection drop → install with `--timeout 120 --retries 10`, use ipykernel instead of jupyter
- Kernel showed MSSQL → installed Python + Jupyter extensions