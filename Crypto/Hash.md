En gros ca permet de vérifier l'intégrité d'un fichier à l'aide d'une fonction de hashage la plus utilisé étant SHA256. Ou encore pour ne pas stocker les mdp en clair mais quand même savoir l'identifié comme les mêmes.

Une collision de hash est quand l'input donne le même output que l'input attendu.

On parle d'effet pigeonhole car il y a plus de pigeon que de nids. 

Pour rendre ca plus dur à cracker on  ajoute au mdp que l'on veut stocker un unique salt. Une chaine de caractere que l'on rajoute à la fin de chaques mdp. 

# Password Cracking
https://hashes.com/en/decrypt/hash
On a déjà utiliser des tables pour cracker les mdp. Mais comment faire lorsqu'il y a du salt ? 
[[Hashcat]] et [[Jhon the Ripper]] sont communément utilisé pour ca.

Hashcat uses the following basic syntax: `hashcat -m <hash_type> -a <attack_mode> hashfile wordlist`, where:

- `-m <hash_type>` specifies the hash-type in numeric format. For example, `-m 1000` is for NTLM. Check the official documentation (`man hashcat`) and [example page](https://hashcat.net/wiki/doku.php?id=example_hashes) to find the hash type code to use.
- `-a <attack_mode>` specifies the attack-mode. For example, `-a 0` is for straight, i.e., trying one password from the wordlist after the other.
- `hashfile` is the file containing the hash you want to crack.
- `wordlist` is the security word list you want to use in your attack.
### HMACs

**HMAC (Keyed-Hash Message Authentication Code)** is a type of message authentication code (MAC) that uses a cryptographic hash function in combination with a secret key to verify the authenticity and integrity of data.

An HMAC can be used to ensure that the person who created the HMAC is who they say they are, i.e., authenticity is confirmed; moreover, it proves that the message hasn’t been modified or corrupted, i.e., integrity is maintained. This is achieved through the use of a secret key to prove authenticity and a hashing algorithm to produce a hash and prove integrity.

The following steps give you a fair idea of how HMAC works.

1. The secret key is padded to the block size of the hash function.
2. The padded key is XORed with a constant (usually a block of zeros or ones).
3. The message is hashed using the hash function with the XORed key.
4. The result from Step 3 is then hashed again with the same hash function but using the padded key XORed with another constant.
5. The final output is the HMAC value, typically a fixed-size string.