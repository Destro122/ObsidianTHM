---
aliases:
  - POP3
---
Permet de téléchargé ses mails depuis son client. [[Simple Mail Transfert Protocol (SMTP)]] est la poste [[Post Office Protocol (POP3)]] va chercher la boite au lettre/

Some common POP3 commands are:

- `USER <username>` identifies the user
- `PASS <password>` provides the user’s password
- `STAT` requests the number of messages and total size
- `LIST` lists all messages and their sizes
- `RETR <message_number>` retrieves the specified message
- `DELE <message_number>` marks a message for deletion
- `QUIT` ends the POP3 session applying changes, such as deletions

Port part défaut : TCP 110
