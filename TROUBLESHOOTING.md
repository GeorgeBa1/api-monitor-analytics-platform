# Troubleshooting

## Secure credential storage unavailable

Εγκατάστησε:

```bash
pip install -r requirements.txt
```

και κάνε restart. Το `keyring` απαιτείται για passwords/webhooks.

## Settings δεν ανοίγει

Έλεγξε ότι τρέχεις τη σωστή έκδοση του project και ότι ο χρήστης έχει ADMIN role.

## SMTP test αποτυγχάνει

Έλεγξε server, port, username/password, TLS requirements και network/firewall.

## Teams test αποτυγχάνει

Έλεγξε webhook, network και ότι το Teams endpoint είναι ενεργό.

## API Authentication αποτυγχάνει

Έλεγξε Login URL, credentials και Token field. Αν η απάντηση είναι `{"access_token":"..."}`, το Token field είναι `access_token`.

## Dashboard δεν έχει δεδομένα

Πάτησε Refresh και βεβαιώσου ότι έχει εκτελεστεί monitoring. Ένα νέο API δεν έχει history μέχρι να γίνει το πρώτο check.

## Timeout / N/A response time

Τα timeout checks θεωρούνται failed/critical και δεν πρέπει να προκαλούν αριθμητικό crash στο alert engine.

**Documentation Version 3.0.0**
