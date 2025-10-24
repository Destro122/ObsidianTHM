John the Ripper est un outils pour crack et [[Brute Force]] de nombreux [[Hash]]
(Dans la suite Jumbo John est utilisé)
[[https://github.com/danielmiessler/SecLists|Seclist]] est une bonne base de donnée de dictionnaire afin de faire des attaques aux dictionnaires. (Ce que l'on fait avec John)

## Cracking Basic Hash
The basic syntax of John the Ripper commands is as follows. We will cover the specific options and modifiers used as we use them.

`john [options] [file path]`

- `john`: Invokes the John the Ripper program
- `[options]`: Specifies the options you want to use
- `[file path]`: The file containing the hash you’re trying to crack; if it’s in the same directory, you won’t need to name a path, just the file.

- `--wordlist=`: Specifies using wordlist mode, reading from the file that you supply in the provided path

https://hashes.com/en/tools/hash_identifier permet de trouver le type de hash d'un fichier. (ou hash identifier sur python)

- `--format=`: This is the flag to tell John that you’re giving it a hash of a specific format and to use the following format to crack it
- `john --list=formats | grep -iF "md5"` to see all the format with md5 

##  Cracking Windows Hash
NTHash / NTLM
-- format="nt"

## Unshadowing

John can be very particular about the formats it needs data in to be able to work with it; for this reason, to crack `/etc/shadow` passwords, you must combine it with the `/etc/passwd` file for John to understand the data it’s being given. To do this, we use a tool built into the John suite of tools called `unshadow`. The basic syntax of `unshadow` is as follows:

`unshadow [path to passwd] [path to shadow]`

- `unshadow`: Invokes the unshadow tool
- `[path to passwd]`: The file that contains the copy of the `/etc/passwd` file you’ve taken from the target machine
- `[path to shadow]`: The file that contains the copy of the `/etc/shadow` file you’ve taken from the target machine

## Using Single Crack Mode
Single crack mode -> partir du nom d'utilisateur pour trouver le mdp 
To use single crack mode, we use roughly the same syntax that we’ve used so far; for example, if we wanted to crack the password of the user named “Mike”, using the single mode, we’d use:

`john --single --format=[format] [path to file]`

- `--single`: This flag lets John know you want to use the single hash-cracking mode
- `--format=[format]`: As always, it is vital to identify the proper format.

## Zip2John

Similarly to the `unshadow` tool we used previously, we will use the `zip2john` tool to convert the Zip file into a hash format that John can understand and hopefully crack. The primary usage is like this:
`zip2john [options] [zip file] > [output file]`

- `[options]`: Allows you to pass specific checksum options to `zip2john`; this shouldn’t often be necessary
- `[zip file]`: The path to the Zip file you wish to get the hash of
- `>`: This redirects the output from this command to another file
- `[output file]`: This is the file that will store the output