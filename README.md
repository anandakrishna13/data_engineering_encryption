# data_engineering_encryption

GPG is very populor encryption tool. It is easy to use and compatible with most of the platforms.

## GPG 
### GPG commands to encrypt and decrypt the file
#### Creating the key.
 RSA (Rivest-Shamir-Adleman) is one of the most widely used way of encryption
 Commands to create keys
 
 ```
  gpg --full-generate-key
 ```
Choose the (1) RSA and RSA in the option.  We can chose default keysize 3072 unless we have specific reason opt other key size
```
What keysize do you want? (3072) 
```
Next parameter is key validity, default option 0, meaning key does not expire. 
We choose other option easily, but we should have proper process to regenerate the keys according to cadanece.
```
Please specify how long the key should be valid.
         0 = key does not expire
      <n>  = key expires in n days
      <n>w = key expires in n weeks
      <n>m = key expires in n months
      <n>y = key expires in n years
Key is valid for? (0) 
```

and provide some idedenty details, email id is very critical, this will used whenever key is used. 
Here is my option
```
GnuPG needs to construct a user ID to identify your key.

Real name: my_company_key
Email address: ananda@example.com
Comment: key
You selected this USER-ID:
    "my_company_key (key) <ananda@example.com>"
```
We can list all key pairs available in our system
```
gpg --list-keys
```

Once key generated, Public key needs tobe exported if we need to share this with other team or system. This command generates the public key file called public_key.asc
```
gpg --export -a ananda@example.com >  public_key.asc
```
Now this is ready to share.

Similarly , get the private key
```
gpg --export-secret-keys -a "<your_email>" > private_key.asc
```

Import the public key, in common practice, this happens in different system, where we want to encrypt the file.
```
gpg --import <public_key_file>
```
Use this command to encrypt any file using the public key,
ex:
```
gpg --recipient ananda@example.com --encrypt sales_data.csv
```

Encrypted file can be decrypted
```
gpg --decrypt sales_data.csv.gpg






 
