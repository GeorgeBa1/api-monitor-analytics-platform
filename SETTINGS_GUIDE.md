# A.P.I. Sentinel 3.0.0 — Settings Guide

## General

- **Timeout (seconds):** μέγιστος χρόνος αναμονής ενός HTTP request. Προτεινόμενο 30–60 sec.
- **Max workers:** πόσα checks μπορούν να τρέχουν παράλληλα. Προτεινόμενο 5–10 για τα περισσότερα περιβάλλοντα.
- **Parallel monitoring:** ON για πολλά APIs· OFF αν θέλεις πιο σειριακή εκτέλεση/troubleshooting.
- **Email notifications:** ON μόνο αν έχεις ρυθμίσει SMTP.
- **Enable Microsoft Teams alerts:** ON μόνο αν έχεις ρυθμίσει Teams webhook.

## SMTP / Email

- **SMTP server:** server του mail provider.
- **Port:** συνήθως 587 για STARTTLS, εκτός αν ο provider απαιτεί άλλη θύρα.
- **Username:** SMTP account.
- **Password:** SMTP password. Κενό σημαίνει «κράτα το υπάρχον».
- **Sender:** διεύθυνση αποστολέα.
- **Recipients:** παραλήπτες, χωρισμένοι με comma ή semicolon.
- **Test SMTP Connection:** δοκιμάζει πραγματικά σύνδεση/authentication.

## Microsoft Teams

- **Enabled:** ενεργοποίηση Teams channel.
- **Failed / Warning / Critical:** φίλτρα για τα αντίστοιχα alert severities.
- **Webhook:** secret Teams webhook. Κενό σημαίνει «κράτα το υπάρχον».
- **Send Test Notification:** στέλνει test message.

## API Authentication

Αφορά login σε **εξωτερικό API**, όχι το login στο Sentinel.

- **Login URL:** endpoint login.
- **Token field:** JSON field που περιέχει το token, π.χ. `token` ή `access_token`.
- **Username / Password:** credentials του εξωτερικού API.

## Ασφάλεια

Passwords, API credentials και webhooks δεν πρέπει να μπαίνουν σε source code ή config files. Το Sentinel χρησιμοποιεί `keyring`/OS credential storage όταν είναι διαθέσιμο.

Αν εμφανίζεται:

`Secure credential storage is unavailable`

εγκατάστησε τα requirements και κάνε restart:

```bash
pip install -r requirements.txt
```

Σε Windows production το τελικό πακέτο πρέπει να χρησιμοποιεί Windows Credential Manager backend.

**Documentation Version 3.0.0**
