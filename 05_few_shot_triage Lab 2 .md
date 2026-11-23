# Step 6: Few-shot on the Same Task

**Project:** ChillarPay AI Support – Zero-shot to Few-shot  
**Course:** Prompt Engineering, AI & Machine Learning | BBA (FinTech), Chitkara Business School  
**Tool used:** Claude (Anthropic)  

## Prompt type: Few-shot (Step 5 prompt + 3 solved examples)

The only change from Step 5 is the three examples.

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

Learn from these examples and follow the same style exactly:

Message: Bhai mere account se ₹3,000 kat gaye, maine koi payment nahi kiya!
Output: Fraud Alert | High | Humein afsos hai. Turant app mein UPI block karein; hamari fraud team ise priority par check kar rahi hai.

Message: Paid ₹450 to a shop, money debited but the shop didn't get it. I want a refund.
Output: Failed Payment | Medium | Sorry for the trouble. Failed payments usually reverse automatically; please share the transaction ID so we can track it.

Message: How do I change my registered email?
Output: Account & KYC | Low | You can update your email under Profile > Settings in the ChillarPay app.

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
| M01 | Failed Payment | Medium | Hi Ananya, sorry for the trouble. Failed payments usually reverse automatically; please share the transaction ID so we can track it. | 21 |
| M02 | Refund | Medium | Hi Rohan, sorry for the wait. Please share your order and transaction ID so we can check the refund status. | 20 |
| M03 | Fraud Alert | High | Hi Priya, we are sorry. Please block UPI in the app now; our fraud team is checking this on priority. | 20 |
| M04 | Account & KYC | High | Hi Sanjay, sorry for the trouble. We are treating your blocked account as priority; please share your registered number to help us verify. | 23 |
| M05 | Account & KYC | Low | You can update your photo and mobile number under Profile > Settings in the ChillarPay app. | 16 |
| M06 | Failed Payment | Medium | We are sorry for the delay. Please share the transaction ID so we can track your stuck payment. | 18 |
| M07 | Failed Payment | Medium | Hi Kavya, sorry for the double charge. Please share both transaction IDs so we can track it. | 17 |
| M08 | Fraud Alert | Low | Thanks for checking. Please do not click the link or share your UPI PIN; ChillarPay never asks for it by SMS. | 21 |
| M09 | Failed Payment | Medium | Aman, humein afsos hai. Failed payments aam taur par apne aap reverse ho jaate hain; kripya transaction ID share karein. | 20 |
| M10 | Account & KYC | Low | Aap app mein Profile > KYC section mein documents ka status dekh sakte hain. Zaroorat ho to documents dobara upload karein. | 21 |
| M11 | Failed Payment | Medium | Humein afsos hai. Kripya transaction ID aur amount share karein taaki hum paise ka status check kar sakein. | 18 |
| M12 | Fraud Alert | High | Humein afsos hai. Turant app mein UPI block karein; hamari fraud team ise priority par check kar rahi hai. | 19 |

## Marking against my answer key (✔ correct / ✘ wrong)

| ID | Category | Priority | Tone | Format (≤25 words, 4 columns) |
|---|---|---|---|---|
| M01 | ✔ | ✔ | ✔ | ✔ |
| M02 | ✔ | ✔ | ✔ | ✔ |
| M03 | ✔ | ✔ | ✔ | ✔ |
| M04 | ✔ | ✔ | ✔ | ✔ |
| M05 | ✔ | ✔ | ✔ | ✔ |
| M06 | ✔ | ✔ | ✔ | ✔ |
| M07 | ✘ | ✔ | ✔ | ✔ |
| M08 | ✔ | ✔ | ✔ | ✔ |
| M09 | ✔ | ✔ | ✔ | ✔ |
| M10 | ✔ | ✔ | ✔ | ✔ |
| M11 | ✔ | ✔ | ✔ | ✔ |
| M12 | ✔ | ✔ | ✘ | ✔ |
| **Total** | **11/12** | **12/12** | **11/12** | **12/12** |

## What I noticed

Rows with a ✘:

- **M07:** category `Failed Payment` (key: `Refund`)
- **M12:** reply tone

Compared with Step 5, the examples fixed the priority of M08, the refund-timing reply in M02, and the English replies to M09 and M11. Two issues remain: M07 is still classed as Failed Payment (the second example treats "debited but not received" as Failed Payment, so the duplicate charge followed that pattern), and the AI copied the example style so closely that it left out the customer's first name in M12.
