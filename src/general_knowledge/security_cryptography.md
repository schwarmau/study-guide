# Security and Cryptography

Most people in the industry aren't designing cyptography algorithms, but there's some value in knowing the uses for the various popular cryptography algorithms and cryptographic schemes in the same way that there's value in knowing some basic malicious attacks against software software systems.

### SHA

An acronym for Secure Hash Algorithms, SHA is a family of cryptographic hash functions, which means that they turn data of arbitrary size into a fixed-size bit array. They are impractical to reverse, and the same data will always result in the same hash, with two values never (or infeasibly) resulting in the same hash. Also, hashes should be unrelated to each other (a small variation in one value should result in a drastically different hash). They are used to verify the integrity of messages and files, as well as for generating and verifying signatures, and verifying passwords. They are also seen used as unique identifiers, and commonly used in software distribution so that users can validate they have the correct file after download by applying the same hash function.

### RSA

RSA is a public-key cryptosystem--a system in which participants have a public encryption key and a private decryption key. It is most commonly used for symmetric key cryptography (keys used for encrypting plaintext and decrypting ciphertext are the same or one is derivative of the other--both keys are known to all the parties participating in the exchange of information), and for small amounts of data in asymmetric key cryptography, because it is a slow algorithm. The premise of such systems is that a party that wants to send a sensitive message to another party can use the latter's public encryption key so that only the latter can decrypt it with their private key. Such systems can also be used in authentication by using the private keys to create digital signatures on messages, and so the receiver can use the sender's public key to re-encrypt the message with the signature and verify that the result is indeed valid.

### Diffie-Hellman Key Exchange

This is a method of securely exchanging cryptographic keys over a public channel. It is itself non-authenticated, but provides the basis for many authenticated protocols.

An underlying assumption is that reversing the operation \\( g^a \mod p \\), where _a_ is some integer, _p_ is a prime number, and _g_ is a primitive root modulo _p_ (math terms; more info [here](https://en.wikipedia.org/wiki/Primitive_root_modulo_n)), is not practical.

The basic algorithm is as follows:
- Alice and Bob publicly agree to use some prime _p_ and some primitive root modulo _p_, _g_.
- Alice secretly chooses an integer, _a_, and sends Bob the result of \\( A = g^a \mod p \\).
- Bob secretly chooses an integer, _b_, and sends Alice the result of \\( B = g^b \mod p \\).
- Alice computes the value of \\( B^a \mod p \\).
- Bob computes the value of \\( A^b \mod p \\).
- The values Alice and Bob computed should be the same, and that is their shared secret.

### HMAC

An HMAC is a Hash-based Message Authentication Code, a specific type of code invoving a cryptographic hash function and a secret cryptographic key. It is used to simultaneously verify the data integrity and authenticity of a message. Such codes can be generated with any cryptographic hash functions (like SHA).

The exact definition/calculation for an HMAC is complex. More info [here](https://en.wikipedia.org/wiki/HMAC).

### AES

AES is a specification for the encryption of electronic data. It describes a symmetric-key algorithm. In practice it is generally superior to RSA for use in a symmetric system, but can be combined with RSA's asymmetric system capabilities such that data is exchanged encrypted via AES, but getting the secret key required to decrypt that data involves authorized recipients publishing a public key and keeping a private key, the public key of which is then used by the sender with RSA to encrypt and transmit secret AES keys to recipients that they can use to decrypt the data.

### Hamming Codification

Hamming codes are a family of linear error-correcting codes that can detect up to two-bit errors or correct one-bit errors without detection of uncorrected errors. Parity bits are a similar concept that cannot correct errors and can only detect an odd number of bits in error. More info [here](https://en.wikipedia.org/wiki/Hamming_code#General_algorithm).

### Cyclic Redundancy Check

Another error-detecting code commonly used in digital networks and storage devices to detect accidental changes to raw data. It is named as such because it expands data without adding information and the algorithm is based on cyclic codes therein. More info [here](https://en.wikipedia.org/wiki/Cyclic_redundancy_check).

## Attack & Defense

There aren't many common attacks that developers will have to actively defend against on a regular basis. From an application design standpoint you could encourage features such as 2-factor authentication, but at the end of the day it's not up to developers whether or not a feature is added. One attack developers will have to actively defend against is the injection attack. Defending against an injection attack is as simple as not letting user input go unchecked to a database query. This means _sanitizing_ and _parameterizing_ user input. Man-in-the-middle attacks are also something that needs to be addressed by developers. The defense against man-in-the-middle attacks is not letting sensitive information travel between services in a manner that makes the information easy to decrypt. In other words: sensitive information should always be encrypted before crossing services, and encrypted information should not travel with or near any information that could aid in decrypting it. While you might not personally have to deal with either of these things, it's not all that common to see a basic injection attack question in an interview (e.g. "What's wrong with this code?").