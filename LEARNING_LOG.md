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

## Lesson 3 – My first model (6 Oct 2026)
**Did:** one-hot encoded the data, split it into train and test, trained a logistic regression, printed readable predictions
**Learned:**
- Models only understand numbers; `pd.get_dummies` turns text columns into 1/0 columns (15 → 46)
- A missing value becomes all zeros in its group (e.g. poutcome all 0 = never contacted)
- Train/test split = mock exam vs real exam; the test set stays hidden while training
- `stratify=y` keeps the yes-rate equal in both halves (11.7%)
- Logistic regression works like a scoring sheet: each column gets points, the total goes through an S-curve to become a probability
- The model learns the points itself with `.fit()`, nudging the weights until its guesses match the real answers
- `predict_proba(...)[:, 1]` gives the chance of yes for each customer
- `random_state=42` makes results repeatable
**Result:** on the first 10 test customers, the 9 who said no got 1–16%, and the one who said yes got 80%
**Problems & fixes:**
- ConvergenceWarning: the model ran out of attempts because columns are on very different scales (balance in thousands vs 0/1 columns). Fix in Lesson 4: scale the data
- Raw probability output was hard to read, so I used a for loop and f-strings to print one sentence per customer
**Question to answer next:** 10 customers isn't enough. How good is the model across all 9,043 test customers?