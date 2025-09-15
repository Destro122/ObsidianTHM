---
aliases:
  - IMAP
---
Imap permet de synchroniser les messages lu, supprimé, déplacé dans toutes les boites mails relié avec [[Post Office Protocol (POP3)]]. Prends plus de place que POP3

- `LOGIN <username> <password>` authenticates the user
- `SELECT <mailbox>` selects the mailbox folder to work with
- `FETCH <mail_number> <data_item_name>` Example `fetch 3 body[]` to fetch message number 3, header and body.
- `MOVE <sequence_set> <mailbox>` moves the specified messages to another mailbox
- `COPY <sequence_set> <data_item_name>` copies the specified messages to another mailbox
- `LOGOUT` logs out
IMAP est sur le port 143 TCP par défaut
