# AI-Assisted Legacy SQL Migration Tool

A small project I built while learning Python and SQL during my MSc in AI at Aston University.

## Why I made this:
In my previous work in fraud investigation, I learned one rule: never trust data without checking it.

AI tools can now rewrite old SQL code very quickly. But can we trust the answer? A query can look perfect and still give different results. I wanted to test this myself.

## What it does
1. I wrote 3 old-style SQL queries
2. I asked an AI (LLM) to rewrite them in modern SQL
3. My code runs the old and new queries on the same small dataset
4. It checks if the results are exactly the same: PASS or FAIL
5. It gives an accuracy score and I note why each test passed or failed

## What I used
- Python and SQLite (in Google Colab)
- Two small tables: `events` and `people`
- Two different prompts, to see if the wording changes the AI's answer:
  - **Prompt A (gentle):** "Rewrite in clean, modern SQL. Keep the results the same."
  - **Prompt B (strict):** "Use JOINs instead of subqueries and name the columns instead of SELECT *."

## Results
| Test | Accuracy |
|---|---|
| Prompt A | 3/3 |
| Prompt B | 3/3 |
| Trap test (a wrong query I added on purpose) | 2/3, caught the mistake ✅ |
All results are in `test_log.csv`.

## What I found
- With the gentle prompt, the AI was correct but hardly changed two of the queries. Safe, but not really modernised.
- With the strict prompt, it properly rewrote all three and was still correct.
- I added a "trap", a JOIN without `DISTINCT`. It showed "London Expo" twice instead of once. My tester caught it, so I know it really works.
- My main takeaway: AI answers can look right but still be wrong, so they should always be tested.

## Limitations
I'm still a beginner, and this is an early version:
- Only 3 queries and a very small dataset
- I collected the AI's answers by hand, not through an API yet
- It only checks the results match, not speed

## What I'd do next
- Add more and harder queries
- Connect to an LLM through an API, so it runs automatically
- Write proper tests with `pytest`

## How to run it
Open the notebook in Google Colab and click **Runtime → Run all**.# AI-Assisted-Legacy-SQL-Migration-Tool
Can we trust AI to rewrite SQL? Compares LLM rewrites with the original query results. 
