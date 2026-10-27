---
type: note
tags: [fix]
service: "[[Roco Mail]]"
---
# SpamAssassin Bayes false positives

## Error

```text
X-Spam-Status: Yes, score=5.8
Content analysis details: (5.8 points, 5.0 required)
SpamAssassin as rocobrok detected message as spam (5.8)
```

## Cause

- cPanel `/etc/mail/spamassassin/CPANEL.cf` raised `BAYES_80`, `BAYES_99`, and `BAYES_999` above SpamAssassin upstream scores. Combined with KAM freemail-number rules, legitimate Gmail messages to `support@rocobroker.com` crossed the 5.0 threshold and Exim routed them to the enabled Spam Box.
- The Bayes database is shared by the whole `rocobrok` account. At diagnosis it contained 248 spam messages, 712 ham messages, and 100,482 tokens.

## Fix

```sh
# /home/rocobrok/.spamassassin/user_prefs
score BAYES_80 2.0
score BAYES_99 3.5
score BAYES_999 0.2
```

- Restored the upstream network-enabled scores only for the `rocobrok` account. Backup: `/home/rocobrok/.spamassassin/user_prefs.pre-bayes-fix-20261027`.
- No Bayes retraining, mail movement, service restart, threshold change, or filter change was performed.

## Verify

- SpamAssassin `--lint` passed.
- Test-mode reports loaded active values `BAYES_80=2.0`, `BAYES_99=3.5`, and `BAYES_999=0.2`.
- The original 5.8 case calculates to 3.6 and the separate 6.8 Bayes case calculates to 4.5, both below the 5.0 threshold with the corrected values.

Fixed on 2026-10-27
