# Step 1: The ChillarPay Case Study

**Project:** ChillarPay AI Support – Zero-shot to Few-shot  
**Course:** Prompt Engineering, AI & Machine Learning | BBA (FinTech), Chitkara Business School  
**Tool used:** Claude (Anthropic)  

## Background

**ChillarPay** is a fictional UPI payments app in Jaipur, used mainly by college students and small shopkeepers. It has 8 lakh users and receives about 2,000 support messages a day in English and Hinglish. Its 6-person support team cannot keep up, and urgent fraud cases get lost among simple questions.

## The question

The Head of Customer Experience asks me, as a Business Analyst:

> **"Can AI sort our messages, set priority and draft replies? When is a simple prompt enough, and when does the AI need examples?"**

## ChillarPay support rules

These rules are used in every step of this project.

| Item | Rule |
|---|---|
| **Categories** | Failed Payment, Refund, Fraud Alert, Account & KYC |
| **High priority** | Money lost without the customer's consent, or account blocked |
| **Medium priority** | Money stuck or delayed, refund pending |
| **Low priority** | Information request or profile update |
| **Reply tone** | Polite and short; use the customer's first name if given; never promise a refund date; reply in Hinglish if the customer writes in Hinglish |

## My approach

1. Create 12 synthetic customer messages with AI (no real data).
2. Write the correct answers myself before testing.
3. Test a zero-shot prompt on a simple task (summarising).
4. Test a zero-shot prompt on the real task (category, priority, reply).
5. Test a few-shot prompt (3 examples) on the same real task.
6. Compare results using a scorecard and recommend a prompt.
