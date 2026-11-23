# ChillarPay AI Support: From Zero-shot to Few-shot Prompting

**A FinTech case study on when a simple prompt is enough and when AI needs examples.**

Author: [Your Name] · BBA (FinTech), Chitkara Business School · Tool: Claude · November 2026

## The case

**ChillarPay** (fictional) is a UPI payments app in Jaipur with 8 lakh users. It receives about 2,000 support messages a day in English and Hinglish, and urgent fraud cases get lost among simple questions. As a Business Analyst, I tested whether AI can sort messages, set priority and draft replies, and what kind of prompt it needs.

## The data

12 synthetic customer messages created with AI (8 English, 4 Hinglish, 3 deliberately tricky). I wrote the correct answers myself before testing.

## Approach

| Step | Prompt type | Task |
|---|---|---|
| 1 | Zero-shot | One-line summary of each message |
| 2 | Zero-shot | Category + priority + reply |
| 3 | Few-shot (3 examples) | Same task as Step 2 |

## Results

| Metric | Zero-shot | Few-shot |
|---|---|---|
| Correct category (/12) | 11 | 11 |
| Correct priority (/12) | 11 | 12 |
| Reply follows ChillarPay tone (/12) | 9 | 11 |
| Table format followed (/12) | 12 | 12 |

## Key learnings

1. **Zero-shot is enough for simple tasks:** all 12 summaries were accurate and within the word limit without any examples.
2. **Few-shot teaches company-specific rules:** it fixed M08 (priority), M02 (no refund time frame), and M09 and M11 (Hinglish replies).
3. **Hinglish and tricky messages:** Hinglish replies improved (M09, M11); the very short message M11 was handled better.
4. **Limitation:** M07 (duplicate charge) was still classed as Failed Payment instead of Refund, and M12 lost the customer's first name because the AI copied the example style too closely.

## My recommendation to ChillarPay

Use the few-shot prompt for daily support, because it follows ChillarPay's priority, tone and language rules more reliably than zero-shot. Keep zero-shot for simple tasks like summaries, and have a human agent check fraud and unclear messages before replies are sent.

## Repository files

| File | Content |
|---|---|
| `01_case_study.md` | ChillarPay case and support rules |
| `02_dataset.md` | Synthetic dataset and answer key |
| `03_zero_shot_summary.md` | Zero-shot summarising |
| `04_zero_shot_triage.md` | Zero-shot triage with marking |
| `05_few_shot_triage.md` | Few-shot triage with marking |
| `06_scorecard.md` | Scorecard and reflection |

## Skills shown

Prompt engineering · Zero-shot and few-shot prompting · Synthetic data creation · AI output evaluation · Customer-support operations · FinTech domain knowledge

## What I learned

- Zero-shot prompting (instructions only) works well for simple, common tasks like summarising.
- Few-shot prompting (instructions + solved examples) teaches AI a company's own rules, tone and format.
- Start with the simplest prompt, and add examples only when the output misses the rules.
- How to create a realistic synthetic dataset with AI, without using real customer data.
- Why the answer key must be written before testing, so AI output is judged fairly.
- How to measure AI quality with a scorecard instead of gut feeling.
- AI output must always be checked by a human before business use.

*ChillarPay and all data in this project are fictional and created for learning.*
