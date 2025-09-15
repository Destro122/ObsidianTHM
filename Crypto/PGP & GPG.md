Pretty Good Privacy (PGP) est un logiciel qui permet de crypter des fichiers, signer ...
GPG est la version open source de PGP.  (Communément utilisé pour les mails).

gpg --full-gen-key : générer une clé gpg
- You would use `gpg --import backup.key` to import your key from backup.key
- To decrypt your messages, you need to issue `gpg --decrypt confidential_message.gpg`