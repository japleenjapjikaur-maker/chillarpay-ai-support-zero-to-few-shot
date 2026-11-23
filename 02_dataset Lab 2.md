# Steps 2 & 3: Synthetic Dataset and Answer Key

**Project:** ChillarPay AI Support – Zero-shot to Few-shot  
**Course:** Prompt Engineering, AI & Machine Learning | BBA (FinTech), Chitkara Business School  
**Tool used:** Claude (Anthropic)  

## Step 2: Dataset created with AI

**Why synthetic data?** Real customer data is private, so the AI was asked to generate realistic but fictional messages. No real names, phone numbers, account numbers or UPI IDs are used.

### Data prompt used

```text
You are helping me build a realistic test dataset for a business case study.

ChillarPay is a fictional UPI payments app in Jaipur used by college students and small shopkeepers. Its support categories are: Failed Payment, Refund, Fraud Alert, Account & KYC.

Create 12 synthetic customer messages that ChillarPay's support team might receive.

Rules:
- Fictional only: no real names, phone numbers, account numbers or UPI IDs.
- 8 messages in English and 4 in Hinglish.
- Cover all 4 support categories.
- Include 3 tricky messages: one that could fit two categories, one that is very short or unclear, and one from an angry customer.
- Do NOT show the category, priority or any reply.

Output a table with these columns: ID (M01 to M12) | Customer message | Channel (App chat / Email / Twitter)
```

### AI output (12 messages)

| ID | Customer message | Channel |
|---|---|---|
| M01 | Hi, I sent ₹1,200 to my landlord through ChillarPay at 9 am. The money left my account but the app shows the payment as failed. Regards, Ananya | App chat |
| M02 | Hello, I cancelled an online order 6 days ago and the refund of ₹899 has still not reached my ChillarPay wallet. Could you please check? - Rohan | Email |
| M03 | I just got a notification that ₹7,500 was sent to 'Kumar Traders'. I NEVER made this payment! Someone has got into my account. - Priya | App chat |
| M04 | Good afternoon, my account has been blocked since this morning and I cannot receive payments at my shop. Please fix this urgently. Sanjay | Email |
| M05 | How can I update my profile photo and mobile number in the app? | App chat |
| M06 | @ChillarPay worst app ever!!! Third time my payment is stuck and nobody replies. Fix this or I'm deleting the app!!! | Twitter |
| M07 | I was charged ₹2,300 twice for the same mobile recharge. One of the amounts should come back to me, please help. - Kavya | App chat |
| M08 | Dear team, I got an SMS saying my KYC will expire and asking me to click a link and enter my UPI PIN. Is this really from ChillarPay? I have not clicked it. | Email |
| M09 | Bhai maine kal ₹600 ka recharge kiya tha, paisa kat gaya par recharge nahi hua. Paisa wapas kab milega? - Aman | App chat |
| M10 | Mera KYC pending dikha raha hai, kitne din mein verify hoga? Kuch aur documents bhi chahiye kya? | Twitter |
| M11 | Paisa gaya, kuch nahi mila | App chat |
| M12 | Mere account se ₹4,200 ki UPI payment hui jo maine kabhi nahi ki. Lagta hai kisi ne mera number use kiya hai. Please jaldi dekhiye. - Neha | Email |

**Dataset check:** 8 English (M01–M08) and 4 Hinglish (M09–M12). Tricky messages: M06 (angry customer), M07 (fits two categories), M11 (very short and unclear).

---

## Step 3: Answer key (written by me before testing)

I applied the ChillarPay rules from `01_case_study.md`. **This key was fixed before running any test prompt and was not changed afterwards.**

| ID | Correct category | Correct priority | Reasoning |
|---|---|---|---|
| M01 | Failed Payment | Medium | Money debited, payment shown as failed: stuck money. |
| M02 | Refund | Medium | Refund pending for a cancelled order: delayed money. |
| M03 | Fraud Alert | High | Unauthorised debit: money lost without consent. |
| M04 | Account & KYC | High | Account blocked. |
| M05 | Account & KYC | Low | Profile update request. |
| M06 | Failed Payment | Medium | Angry customer, payment stuck: delayed money. |
| M07 | Refund | Medium | Tricky (could be Failed Payment or Refund). Customer wants the extra charge returned, so Refund. |
| M08 | Fraud Alert | Low | Phishing attempt reported, no money lost, no block: information request. |
| M09 | Failed Payment | Medium | Recharge failed, money debited: stuck money. |
| M10 | Account & KYC | Low | KYC information request. |
| M11 | Failed Payment | Medium | Tricky (very short). Money gone, nothing received: treated as a stuck payment. |
| M12 | Fraud Alert | High | Unauthorised debit: money lost without consent. |
