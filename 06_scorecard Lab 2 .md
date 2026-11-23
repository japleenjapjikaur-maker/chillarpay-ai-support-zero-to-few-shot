# Step 7: Scorecard and Reflection

**Project:** ChillarPay AI Support – Zero-shot to Few-shot  
**Course:** Prompt Engineering, AI & Machine Learning | BBA (FinTech), Chitkara Business School  
**Tool used:** Claude (Anthropic)  

## Scorecard

Scores are taken from the ✔ / ✘ marking tables in `04_zero_shot_triage.md` and `05_few_shot_triage.md`.

| What I checked | Zero-shot (Step 5) | Few-shot (Step 6) |
|---|---|---|
| Correct category (out of 12) | 11 | 11 |
| Correct priority (out of 12) | 11 | 12 |
| Reply follows ChillarPay tone (out of 12) | 9 | 11 |
| Table format followed (out of 12) | 12 | 12 |
| **Total (out of 48)** | **43** | **46** |

## Reflection

1. **Where was zero-shot good enough?** In Step 4 (summarising), all 12 summaries were accurate and within 12 words. Summarising is a common task that needs no ChillarPay rules, so instructions alone were enough.

2. **Which messages did few-shot fix?** M08 (priority corrected from High to Low), M02 (no refund time frame mentioned), and M09 and M11 (replies now in Hinglish). Category score stayed 11/12.

3. **Did Hinglish and tricky messages improve?** Hinglish improved: M09 and M11 moved from English to Hinglish replies, while M10 and M12 were already fine. Of the tricky messages, M11 improved, M06 stayed correct, and M07 stayed wrong (Failed Payment instead of Refund). Also, M12 lost the customer's first name because the AI copied the example style too closely.

4. **Recommendation:** I would use the few-shot prompt for daily support, because it follows ChillarPay's priority, tone and language rules more reliably (tone 9/12 to 11/12). Zero-shot is fine for summaries. A human agent should still check fraud and unclear cases before replies go out.
