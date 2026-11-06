# Zava – zasady klasyfikacji zgłoszeń IT (Zava IT triage rules)


## Format odpowiedzi
Zwróć **wyłącznie** poprawny JSON z czterema polami:

```json
{"category": "...", "priority": "P1|P2|P3|P4", "team": "...", "summary_pl": "..."}
```

## 1. Kategorie i zespoły

| System / temat zgłoszenia | category | team |
|---|---|---|
| VPN, Wi-Fi, sieć | Network | Network Team |
| Laptop, monitor, stacja dokująca, telefon, słuchawki | Hardware | Workplace |
| Drukarki, skanery, toner | Printing | Workplace |
| Konto, hasło, MFA, uprawnienia | Access | Service Desk |
| Outlook, Teams, SharePoint, OneDrive | Email & Collaboration | Service Desk |
| CRM, Jira, Portal HR, Intranet | Business Applications | Application Support |
| SAP, KSeF oraz **każde zgłoszenie dotyczące faktur** | Finance Systems | Finance IT |
| Incydenty bezpieczeństwa (phishing, malware, utrata/kradzież sprzętu, wyciek danych, podejrzane logowanie, udostępnione hasło) | Security | Security Operations |

**Reguła faktur:** jeśli zgłoszenie dotyczy faktur, kategoria to Finance Systems – nawet gdy problem dotyczy Outlooka, Teams, drukarki lub Excela.
**Wyjątek:** incydent bezpieczeństwa ma zawsze pierwszeństwo (np. phishing „z fakturą” → Security).

## 2. Priorytety – stosuj reguły w tej kolejności (pierwsza pasująca wygrywa)

1. Incydent bezpieczeństwa → **P1**
2. Drukowanie → **P4**; jeśli problem dotyczy wielu osób (całe piętro, biuro) → **P3**. Drukowanie nigdy nie ma P1 ani P2.
3. Awaria dotycząca wielu użytkowników (cały zespół, dział, piętro, biuro, grupa osób) → **P1**
4. Prośba, zamówienie lub pytanie („proszę o…”, „jak…?”) → **P4**
5. Finance Systems: **P2** w okresie zamknięcia miesiąca (dzień 25–31), w pozostałe dni **P3**
6. Problem z VPN: zgłaszający **Manager lub Executive → P2**, **Employee → P3**
7. Jeden użytkownik całkowicie nie może pracować → **P2**
8. Jeden użytkownik, praca możliwa (obejście, spowolnienie, drobna usterka) → **P3**

Rola zgłaszającego wpływa na priorytet **tylko** w regule VPN.

## 3. Styl pola summary_pl
- Zawsze **po polsku**, maksymalnie **20 słów**.
- Zaczyna się od nazwy systemu w nawiasach kwadratowych, np. `[VPN]`, `[Outlook]`, `[Bezpieczeństwo]`, `[Faktury]`.
- Opisuje problem, nie osobę: **bez imion, nazwisk, numerów telefonów, e-maili, PESEL**.
- Styl rzeczowy, bez zwrotów grzecznościowych.

## Przykład
Zgłoszenie: „Nie mogę wysyłać maili – każda wiadomość wraca z błędem 550.” (Employee, 2026-11-16)

```json
{"category": "Email & Collaboration", "priority": "P2", "team": "Service Desk", "summary_pl": "[Outlook] Wszystkie wysyłane wiadomości wracają z błędem 550."}
```
