[title]: # (Password Reset Server Encryption)
[tags]: # (password)
[priority]: # (1)
# Password Reset Server Encryption

Password Reset Server utilized two cryptographic algorithms for storing its data: AES-256 and SHA-512.

## AES-256 (Advanced Encryption Standard)

Password Reset Server uses the government standard AES-256 algorithm for storing domain passwords.
When entering the password for a domain account that will be used for changing passwords, Password
Reset Server will encrypt it using the AES-256 algorithm. For more information on AES, please see the
[official standard](https://csrc.nist.gov/csrc/media/publications/fips/197/final/documents/fips-197.pdf).

## SHA-512 (Secure Hash Algorithm)

Password Reset Server utilized SHA-512, an irreversible data transformation to securely store local account passwords and answers to questions. Hashing algorithms are mathematical functions to replace inputted text values with numerical ones. If the input text is the same, the final hashed value will also be the same. The input text of fox will always produce the same hashed value. Minor changes in the input value will radically alter the hashed output,as shown in the examples below.

__Example input text:__ The quick brown fox jumps over the lazy dog

__Hashed value:__ 07e547d9 586f6a73 f73fbac0 435ed769 51218fb7 d0c8d788 a309d785 436bbb64
2e93a252 a954f239 12547d1e 8a3b5ed6 e1bfd709 7821233f a0538f3d b854fee6

__Example input text, with 'dog' changed to 'cog':__ The quick brown fox jumps over the lazy cog.

__Hashed value:__ 3eeee1d0 e11733ef 152a6c29 503b3ae2 0c4f1f3c da4cb26f 1bc1a41f 91c7fe4a
b3bd8649 4049e201 c4bd5155 f31ecb7a 3c860684 3c4cc8df cab7da11 c8ae5045

## SSL/TLS (Secure Socket Layer)

Password Reset Server can be configured to run SSL certificates. It is strongly recommended that
Password Reset Server installations run using SSL. Not using SSL will significantly reduce the security of
the contents of Password Reset Server since browsers viewing the site will not be using an encrypted
connection. 
