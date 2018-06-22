# Cryptography and PKI

When data is transmitted over untrusted networks it has to be encrypted.

* sender cannot deny he sended the data: authenticity of sender **Digital Signature**
* data cannot be read by anyoone else: confidentiality  **Encryption**
* data cannot be altered by anyone: Integrity **Hashing**

**Symmetric key encryption**: when to encrypt and decrypt data same key is used

           Sender----------------------------------->Reciever
           data->encrypted data                      encrypted data-> data
           Key1                                      Key1
	
**Assymetric key encryption**: when to encrypt data and decrypt data two differnet keys are used, to encrypt data Reciever's public key is used at sender's end, to decrypt data recievers private key is used

           Sender S1--------------------------------> Reciever R1
           data->encrypted data                       encrypted data->data
           PubKeyR1                                   PrivKeyR1

**Digital Signatures**:

	   Sender S1--------------------------------> Reciever R1
           data->encrypted data                       encrypted data->data
           PrivKeyS1                                  PublicKeyS1

Since Public is open to everyone, any person can use other's public key and can tell sender to send message encrypting with this key.
to be sure the one who is claiming the public key is its own CA comes into picture.

**Certificate Authority**: One who gives a certifies the public key
it certifies the public key of Alice and encrypt it using own private key. one who wants to send message to alice has to download certificate of Alice decrypt it using CA's public key and get the public of Alice.

*Generating CA and own PKI*
https://www.digitalocean.com/community/tutorials/openssl-essentials-working-with-ssl-certificates-private-keys-and-csrs
