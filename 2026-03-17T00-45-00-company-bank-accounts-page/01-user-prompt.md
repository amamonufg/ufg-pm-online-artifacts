![01-user-prompt-image-01.png](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/01-user-prompt-image-01.png)

On the company bank accounts page following changes are proposed:

1. Rename Company Bank Fccounts → Internal Company Bank Accounts (header, nav menu title, where applicable)
2. Add account number field
3. Render company name value in company column (now shows company short code)
4. Adjust column order: 1) Company (renders company name), 2) Company Code (renders company short code), 3) Bank name, 4) Account name, 5) Account short code, 6) Account currency, 7) Account number, 8) IBAN, 9) Status, 10) Actions.

![01-user-prompt-image-02.png](https://raw.githubusercontent.com/amamonufg/ufg-pm-online-artifacts/main/2026-03-17T00-45-00-company-bank-accounts-page/01-user-prompt-image-02.png)

On the company bank account form page following changes are proposed:

1. Add new field - Correspondent account
2. Change field order: 1) Company, 2) Bank name, 3) Account name, 4) Short code, 5) Account currency, 6) Account number, 7) Correspondent account number, 8) IBAN, 9) SWIFT, 10) Address, 11) Active flag
3. Instead of having active flag (which just reflects account state), we need a way to indicate several states that can happen to bank account: 1) account termination (with termination date and notes), 2) account suspension / block (with block date and notes), 3) account suspension lifted / block removed.