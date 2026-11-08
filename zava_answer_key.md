# Zava ticket dataset – answer key (instructor only)

`zava_train.jsonl` has **100 lines**: 97 unique tickets + 3 duplicate lines. **20 lines contain a defect.**

| Line | Ticket ID | Defect type | What is wrong | Fix |
|---|---|---|---|---|
| 7 | TR-007 | Wrong label – category | Invoice ticket mentioning Outlook/mailbox labelled Email & Collaboration (invoice rule ignored) | category → Finance Systems, team → Finance IT |
| 9 | TR-009 | Style violation | summary_pl written in English and without the [System] tag | Rewrite in Polish: [Bezpieczeństwo] Seria niezamówionych powiadomień MFA; możliwa próba przejęcia konta. |
| 11 | TR-011 | Personal data (GDPR) | Full name and private phone number in the ticket text; name also copied into summary_pl | Mask or remove personal data in the user message; remove the name from summary_pl |
| 22 | TR-022 | Wrong label – category | VPN ticket labelled as Hardware | category → Network |
| 23 | TR-023 | Wrong label – team | SAP/invoice ticket routed to Application Support | team → Finance IT |
| 25 | TR-025 | Invalid JSON | Trailing comma before closing brace | Remove the trailing comma |
| 26 | TR-026 | Personal data (GDPR) | Full name and phone number and e-mail in the ticket text; name also copied into summary_pl | Mask or remove personal data in the user message; remove the name from summary_pl |
| 34 | TR-006-dup | Exact duplicate | Exact copy of TR-006 | Delete the line |
| 36 | TR-035 | Style violation | summary_pl too long (29 words, limit 20) and without the [System] tag | Shorten: [Bezpieczeństwo] Były pracownik nadal ma dostęp do kanału zespołu w Teams. |
| 39 | TR-038 | Invalid JSON | Missing closing brace | Add the closing brace |
| 43 | TR-042 | Wrong label – priority | Security incident labelled P3 (rule: security always P1) | priority → P1 |
| 46 | TR-045 | Personal data (GDPR) | Full name and PESEL number in the ticket text; name also copied into summary_pl | Mask or remove personal data in the user message; remove the name from summary_pl |
| 47 | TR-046 | Invalid JSON | Single quotes instead of double quotes | Use double quotes |
| 51 | TR-050 | Wrong label – priority | Single-user printing problem labelled P2 (rule: printing max P4 / P3 if many users) | priority → P4 |
| 62 | TR-028-dup | Exact duplicate | Exact copy of TR-028 | Delete the line |
| 66 | TR-064 | Wrong label – category | Teams ticket labelled as Business Applications | category → Email & Collaboration |
| 73 | TR-071 | Missing field | Field 'team' is missing | Add team → Security Operations |
| 89 | TR-054-conflict | Conflicting duplicate | Same ticket as TR-054 but with priority P3 instead of P1 | Delete the line (keep the correct original) |
| 93 | TR-090 | Wrong label – priority | VPN problem from an Employee labelled P2 (rule: Employee VPN = P3) | priority → P3 |
| 100 | TR-097 | Wrong label – team | Security incident routed to Service Desk | team → Security Operations |

## Scoring suggestion
- 1 point for each defect found and fixed correctly; personal data counts double (3 lines × 2).
- Maximum: 23 points.
- Bonus discussion: label errors (wrong category/priority/team) are invisible to a format checker – only a human or an LLM judge that knows the rules will find them.

## Summary by type
- Wrong label – category: 3
- Style violation: 2
- Personal data (GDPR): 3
- Wrong label – team: 2
- Invalid JSON: 3
- Exact duplicate: 2
- Wrong label – priority: 3
- Missing field: 1
- Conflicting duplicate: 1
