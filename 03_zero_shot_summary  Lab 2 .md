# Step 4: Zero-shot on a Simple Task (Summarising)

**Project:** ChillarPay AI Support – Zero-shot to Few-shot  
**Course:** Prompt Engineering, AI & Machine Learning | BBA (FinTech), Chitkara Business School  
**Tool used:** Claude (Anthropic)  

## Prompt type: Zero-shot (instructions only, no examples)

```text
Summarise each ChillarPay customer message below in one short line (maximum 12 words).

Output a table: ID | Summary

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

| ID | Summary | Words |
|---|---|---|
| M01 | ₹1,200 rent payment shows failed but money was deducted. | 9 |
| M02 | Refund of ₹899 for cancelled order not received. | 8 |
| M03 | Unauthorised ₹7,500 transfer; customer suspects account was accessed. | 8 |
| M04 | Account blocked; shopkeeper cannot receive payments. | 6 |
| M05 | Asks how to change profile photo and mobile number. | 9 |
| M06 | Angry about repeated stuck payments and no support reply. | 9 |
| M07 | Charged ₹2,300 twice for one recharge; wants one returned. | 9 |
| M08 | Received suspicious KYC SMS asking for UPI PIN; asks if genuine. | 11 |
| M09 | Recharge failed after ₹600 deducted; asks when refund arrives. | 9 |
| M10 | KYC shows pending; asks time needed and extra documents. | 9 |
| M11 | Money deducted but nothing received; details unclear. | 7 |
| M12 | Unauthorised ₹4,200 UPI payment; suspects number misuse. | 7 |

## What I noticed

The summaries are accurate and every one stays within 12 words, so instructions alone were enough for this common task. Summarising needs no company rules, so the AI did not need examples.
