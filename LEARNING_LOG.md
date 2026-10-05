## Lesson 1 – Setup & first look at the data (5 Oct 2026)
**Did:** set up venv, installed libraries, loaded UCI Bank Marketing data
**Learned:** features (X) vs target (y), class imbalance (11.7% yes), data leakage (`duration`)
**Problems & fixes:**
- Git Bash needs `source .venv/Scripts/activate` (forward slashes)
- Connection drop → install with `--timeout 120 --retries 10`, use ipykernel instead of jupyter
- Kernel showed MSSQL → installed Python + Jupyter extensions

## Lesson 2 – What drives a yes? (5 Oct 2026)
**Did:** created a 1/0 `subscribed` column, compared yes-rates with groupby, tested combined filters
**Learned:**
- Average of 1s and 0s = yes-rate
- groupby works like an Excel pivot table
- `&` combines conditions; `len()` counts rows
- Rate × size matters; manual filters miss most yeses
**Problems & fixes:**
- groupby drops NaN by default, so check what's missing