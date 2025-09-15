RSA est un cipher protocol [[Asymmetric Encryption]].
Il se base sur la multiplication de grand nombre premier. (autour de 300 chiffres)
Ce qu'il faut savoir pour RSA : 
- p and q are large prime numbers
- n is the product of p and q
- The public key is n and e
- The private key is n and d
- m is used to represent the original message, i.e., plaintext
- c represents the encrypted text, i.e., ciphertext
  
Logiciel pour les CTFs :  
[RsaCtfTool](https://github.com/Ganapati/RsaCtfTool)
[rsatool](https://github.com/ius/rsatool)