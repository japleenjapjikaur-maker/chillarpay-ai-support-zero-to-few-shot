# Step 5: Zero-shot on the Real Business Task

**Project:** ChillarPay AI Support – Zero-shot to Few-shot  
**Course:** Prompt Engineering, AI & Machine Learning | BBA (FinTech), Chitkara Business School  
**Tool used:** Claude (Anthropic)  

## Prompt type: Zero-shot (rules in words, no examples)

```text
You are a customer-support assistant for ChillarPay, a UPI payments app.

For each customer message below, give:
1. Category: one of Failed Payment, Refund, Fraud Alert, Account & KYC
2. Priority: High, Medium or Low, using this rule:
   High = money lost without the customer's consent, or account blocked
   Medium = money stuck or delayed, refund pending
   Low = information request or profile update
3. Reply: a reply in ChillarPay's tone: polite and short; use the customer's first name if given; never promise a refund date; reply in Hinglish if the customer writes in Hinglish.

Output a table: ID | Category | Priority | Reply (maximum 25 words)

Messages:

M01: Hi, I sent ₹1,200 to my landlord through ChillarPay at 9 am. The money left my account but the app shows the payment as failed. Regards, Ananya
M02: Hello, I cancelled an online order 6 days ago and the refund of ₹899 has still not reached my ChillarPay wallet. Could you please check? - Rohan
M03: I just got a notification that ₹7,500 was sent to 'Kumar Traders'. I NEVER made this payment! Someone has got into my account. - Priya
M04: Good afternoon, my account has been blocked since this morning and I cannot receive payments at my shop. Please fix this urgently. Sanjay
M05: How can I update my profile photo and mobile number in the app?
M06: @ChillarPay worst app ever!!! Third time my payment is stuck and nobody replies. Fix this or I'm deleting the app!!!
M07: I was charged ₹2,300 twice for the same mobile recharge. One of the amounts should come back to me, please help. - Kavya
M08: Dear team, I got an SMS saying my KYC will expire and asking me to click a link and enter my UPI PIN. Is this really from ChillarPay? I have not clicked it.
M09: Bhai maine kal ₹600 ka recharge kiya tha, paisa kat gaya par recharge nahi hua. Paisa wapas kab milega? - Aman
M10: Mera KYC pending dikha raha hai, kitne din mein verify hoga? Kuch aur documents bhi chahiye kya?
M11: Paisa gaya, kuch nahi mila
M12: Mere account se ₹4,200 ki UPI payment hui jo maine kabhi nahi ki. Lagta hai kisi ne mera number use kiya hai. Please jaldi dekhiye. - Neha
```

## AI output

| ID | Category | Priority | Reply (max 25 words) | Words |
|---|---|---|---|---|
| M01 | Failed Payment | Medium | Hi Ananya, sorry for the inconvenience. Please share your transaction ID so we can check; failed payments usually reverse automatically. | 20 |
| M02 | Refund | Medium | Hi Rohan, thanks for reaching out. Refunds usually reflect within 5–7 working days, and we will check your refund status and update you shortly. | 24 |
| M03 | Fraud Alert | High | Hi Priya, we are very sorry about this. Please block UPI in the app immediately; our fraud team will investigate urgently. | 21 |
| M04 | Account & KYC | High | Hi Sanjay, sorry for the disruption. We have marked your blocked account as urgent and our team will review it shortly. | 21 |
| M05 | Account & KYC | Low | You can update your photo and mobile number from the Profile section of the app. Number changes may need OTP verification. | 21 |
| M06 | Failed Payment | Medium | We are sorry for the frustration. Please share the transaction ID and we will look into your stuck payment right away. | 21 |
| M07 | Failed Payment | Medium | Hi Kavya, sorry about the duplicate charge. Please share both transaction IDs and we will investigate and update you. | 19 |
| M08 | Fraud Alert | High | Thank you for flagging this. Please do not click the link or share your UPI PIN; ChillarPay never asks for it over SMS. | 23 |
| M09 | Failed Payment | Medium | Hi Aman, sorry for the trouble. Please share the transaction ID and we will check your recharge and refund status. | 20 |
| M10 | Account & KYC | Low | Aapka KYC verification process mein hai. Kripya apne documents app mein upload karein ya status check karein. | 17 |
| M11 | Failed Payment | Medium | Sorry to hear that. Could you please share the transaction ID and amount so we can check? | 17 |
| M12 | Fraud Alert | High | Neha ji, humein khed hai. Kripya turant apna UPI block karein; hamari fraud team ise jaldi dekh rahi hai. | 19 |

## Marking against my answer key (✔ correct / ✘ wrong)

| ID | Category | Priority | Tone | Format (≤25 words, 4 columns) |
|---|---|---|---|---|
| M01 | ✔ | ✔ | ✔ | ✔ |
| M02 | ✔ | ✔ | ✘ | ✔ |
| M03 | ✔ | ✔ | ✔ | ✔ |
| M04 | ✔ | ✔ | ✔ | ✔ |
| M05 | ✔ | ✔ | ✔ | ✔ |
| M06 | ✔ | ✔ | ✔ | ✔ |
| M07 | ✘ | ✔ | ✔ | ✔ |
| M08 | ✔ | ✘ | ✔ | ✔ |
| M09 | ✔ | ✔ | ✘ | ✔ |
| M10 | ✔ | ✔ | ✔ | ✔ |
| M11 | ✔ | ✔ | ✘ | ✔ |
| M12 | ✔ | ✔ | ✔ | ✔ |
| **Total** | **11/12** | **11/12** | **9/12** | **12/12** |

## What I noticed

Rows with a ✘:

- **M02:** reply tone
- **M07:** category `Failed Payment` (key: `Refund`)
- **M08:** priority `High` (key: `Low`)
- **M09:** reply tone
- **M11:** reply tone

The AI handled the clear English messages well. It struggled where ChillarPay's own rules matter: it chose a different category for the duplicate-charge message, rated the phishing SMS (no money lost) as High, mentioned a refund time frame in M02, and replied in English to the Hinglish messages M09 and M11.
