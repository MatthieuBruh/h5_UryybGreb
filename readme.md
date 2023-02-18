<h1 align="center"><a href="https://www.haaga-helia.fi/en">Haaga-Helia</a> - <a href="https://terokarvinen.com/2023/information-security-2023/">Information Security</a> - H5 Uryy Greb</h1>
<h2 align="center">Matthieu Brühwiler - February 2023</h2>
<br>

## Table of Contens
1. [ Schneier 2015 - Summary. ](#schneider)
2. [ Password Manager - Exaplain. ](#passManEx)
3. [ Password Manager - Demonstrate. ](#passManDem)
4. [ Message - Encrypt and Decrypt. ](#message)
<br>

----
<a name="schneider"></a>
# 1. Schneier 2015: Applied Cryptography
## [10.1 CHOOSING AN ALGORITHM](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/19_chap10.html#chap10-sec001)
* To choose an algorithm, you have several alternatives:
  * Choose a published algorithm that has not been broken, and hoping that a published algorithm is strong enough.
  * Can trust a manufacturer that has a good reputation, and that the latter provides strong algorithms to maintain his reputation.
  * Can trust a private consultant, hoping for the latter is impartial and equipped enough to make a reliable evaluation.
  * Can trust a government, hoping for the confident in it and that the latter would not lie to its citizens.
  * Choose to create an algorithm its own, because it is not safe enough to trust another entity.
* Whatever is your choice, each alternative is problematic.
  * Trusting only one entity may generate trouble, because an entity always has its own interest.
  * Whoever you are, writing your own algorithm without third-party testing does not make sense.
* One huge problem with algorithm is the fact that we do not know all the capabilities of each organization, such as the NSA.
  * Whatever you do for getting arrested, and you use an encrypted computer, any organization (such as the FBI) pretends that they succeeded to decrypt your computer (so, to break the algorithm). It is because their capabilities are more secret and important than your crime.
  * You need to be very performant to get the NSA admitted that they can break an algorithm.
* It is good to admit that the NSA can read any message that it chooses. However, it cannot read all the messages.
  * Even the biggest organizations have limited resources and various targets.
* One of the best things that we can do is to choose public algorithms that has resisted to enough public test and cryptanalysis.
* All the algorithms that have to be exported outside the United States must be approved by the NSA.
  * The NSA is able to break all the exported-approved algorithm. However, it is not an official source!! This rumour comes from the private suggests made by the NSA to the private companies. The suggests can include: leaking a key bit once in a while, use a fixed IV; or encrypt a fixed header; generate randomly few bytes, encrypt them and add the both at the beginning of the message.
  * The NSA keeps a copy of the source-code of each export-approved algorithm. So, BEWARE of encryption algorithms from the U.S.

## [10.2 PUBLIC-KEY CRYPTOGRAPHY VERSUS SYMMETRIC CRYPTOGRAPHY](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/19_chap10.html#chap10-sec002)
* Is is not possible to compare on an equal footing public-key cryptography and symmetric cryptography.
* Needham and Schroeder, highlighted that public-key algorithms generate a larger number of longer messages compared to symmetric algorithms.
  * As a result, they concluded that symmetric algorithms were more efficient than public-key algorithms.
  * However, their analysis failed to consider the significant security advantages that come with public-key cryptography.
* Whitfield Diffie says:
  * Public-key cryptography was initially viewed as a new form of cryptosystem and faced criticism regarding its security and performance.
  * RSA system was around 1/1000th as fast as DES and required ten times larger keys, leading to doubts about the feasibility of public-key cryptography.
  * The idea of using public-key systems for exchanging keys for conventional (symmetric) cryptography was present from the beginning but wasn't initially recognized as necessary.
  * Hybrid systems were proposed as a solution, which combined both public-key and symmetric cryptography, and were considered a significant breakthrough in the field.
* Public-key cryptography and symmetric cryptography are different
  * They solve different kind of problems.
    * Symmetric cryptography: encrypting data
    * Public-key cryptography: best for key management and a multitude of protocols

## [10.3 ENCRYPTING COMMUNICATIONS CHANNELS](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/19_chap10.html#chap10-sec003)
* Alice wants to send a secure message to Bob. To secure the message she encrypts it.
* Theoretically, the encryption can be at any layer of the OSI model.
* In practice, the encryption is at the two lowest layer level (*link-by-link encryption*) or at the highest layer level (*end-to-end encryption*).
* **Link-by-link encryption**
  * The physical layer is the easiest place to add the encryption.
  * The interfaces of the physical layer are standardized, so it is easy to connect hard device encryption.
  * All the data (message, protocols, routing, etc.) are encrypted when they go through the interface.
    * Each time before processing, the whole data needs to be decrypted.
  * Effective because everything is encrypted, no information can be taken without decrypting the message.
  * Traffic-flow security is when the attacker is not able to access to the content of the message and the metadata of this latter.
  * As regards the key management, only two endpoints need a common key.
  * Synchronous communications line can be encrypted using 1-bit CFB, which can recover from errors automatically and encrypts only when messages are sent.
  * Asynchronous communications line can also use 1-bit CFB, but the adversary can get information about the rate of transmission. Passing dummy messages during idle times can help conceal the information.
  * Encryption at the physical layer requires encrypting each physical link in the network and protecting every node in the network, which can be costly and difficult to manage.
  * Link-by-link encryption provides security but can be expensive and difficult to implement for large networks with multiple users and nodes. Table 10.2 summarizes the pros and cons of this type of encryption.
* **End-to-End Encryption**
  * Add encryption between the network layer and the transport layer.
  * We only encrypt the transport data, and routing information is not encrypted. So, the **traffic analysis** is not "blocked".
  * Avoid the encryption / decryption that is required with link-by-link encryption.
  * However, we can learn a lot with the data that is not encrypted, like the sender and the receiver.
  * Building an end-to-end encryption is difficult, because of the different communication protocols.
  * If we encrypt a higher layer (application/presentation), the encryption is independent of the used communication network.
  * Encryption can be directly embedded in the software or in specialized hardware.
* **Combining the Two**
  * Combining the two is more expensise, but it is the most effective way of securing a network.
  * The encryption of the physical link makes the routing analysis impossible, and the end-to-end encryption reduce the risk of unencrypted data.
  * The two key management systems can be completely isolated.

## [10.4 ENCRYPTING DATA FOR STORAGE](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/19_chap10.html#chap10-sec004)
* We can also use encryption to store data securely.
* Applications that are used for data storage must have some mechanisms to avoid an unrecoverable data situation.
* Cryptography converts long secret key as a smaller secret key, so it is also easier to lose it.
* When storing encrypted data, the key management has to take in consideration that we will use the key several times.
* A key used to store encrypted must assume that it will be stored securely for many years.
* There are some problems related to encrypt data for storage, such as:
  * I/O devices require fast encryption, so high-speed algorithms may be required. Hardware encryption can also be required.
  * It is important to keep your keys in a safe place.
  * Key management is more complicated, because multiple person will want to access to different parts of the storage and over the years.
* It is easier to retrieve files that are not structured, such a text file.
* Encrypting database files is problematic:
  * Encrypting each row independently is more susceptible to a block-replay attack.
  * It is inefficient to decrypt a whole database to access only one row.
* It is important to be sure the unencrypted version of a file is completely deleted after the encryption.
* **Dereferencing Keys**
  * When you want to encrypt a hard drive, you can encrypt all the data using a single key, or you can encrypt each file with a different key.
  * The single key method does not allow you to give access to a single part to a user.
  * The second method requires the user to remember all the different keys.
  * The best solution is to encrypt each file with a different key and then to encrypt this file with another key. So, you only need to remember one key.
    * With this method, you can create subfiles that contains only the key related to a user.
<br>

----
<a name="passManEx"></a>
# 2. Password Manager - Explain
As a password manager, I choose the [Norton Password Manager](https://us.norton.com/). It is a cloud-based password manager that enable us to create, store and manage our passwords. It is also able to manage wallets, addresses and other notes.

## What treaths does it protect against?
The Norton Password Manager (NPM) offers several features against different kind of attacks.
* With NPM, you can create **stong**, **unique** passwords for each of your accounts. This avoids having your accounts stolen because of **weak passwords**.
* It provides a feature that fills automatically your login credentials on **verifired** and **authentic** website. It prevent the fact that you provide your credentials to a **phishing** website.
* Automatic filling of your credentials also avoids **keylogging** situation. In fact, you don't need to rewrite your password or to copy-paste it. It is automatically managed by NPM.
* To transmit login credentials, NPM by using secure connection and by verifying the website before auto-filling. This makes it possible to avoid **man-in-the-middle attacks**.
* NPM can prevent users when his/her data is detected in **data breach**. So, the user is prompted to change the concerned password(s).
* NPM is also able to scan your passwords to ensure that they are unique. It avoids **credentials stuffing**.

## What information is encrypted, what's not?
According to Norton's website, all sensitive data is encrypted with AES-256. Sensitive data includes: login credentials, personal information, and payment details. In other words, Norton says that all the data stored in NPM is encrypted.

## What's the license? How would you describe license's effects or categorize it?
NPM is licensed as a shareware. It means that it is a proprietary software that is shared by the owner for small or no cost. Usually, a shareware has limited functionalities or an incomplete documentation as long as you don't pay for it.
In the case of NPM, you can use it for free and have an unlimited number of passwords and devices.
However, the shareware license does not offer the benefits of an open-source software. Indeed, the source code is not accessible, and therefore cannot be corrected or improved by the community. Unlike open-source password management, the software is not transparent and we can only believe in what Norton says.

## Where is the data stored? If in "the cloud", which country / juristiction / which companies? If on local disk, where?
Norton Password manager is a cloud-based password manager. Norton saves data all around the world (United States, Canada, and the European Union) using the servers of NortonLifeLock Inc.
Norton Privacy policy says that Norton is committed to responding to General Data Protection Regulation (GDPR) in the European Union.
It is also important to note that the Norton's privacy point that Norton may use third-party service to assist in providing the Norton Password Manager service. These providers can be located in several countries.

## How is the data protected?
* As said before, NPM uses 256-bit AES encryption.
  * It is the same encryption that is used in financial institutions, such as banks.
* The NPM encryption ensures that data is secured in transit and at rest.
* NPM provides Two-Factor Authentication to add an additional security layer to protect user accounts.
* NPM also provides Advanced Access Controls, which prevent unauthorized access to user data, the use of strong passwords, and IP address restrictions.
* Norton also monitors system for any suspicious activity.

## Sources
* [PCMag UK - Norton Password Manager](https://uk.pcmag.com/password-managers/117939/symantec-norton-password-manager)
* [Norton - Password Manager](https://us.norton.com/feature/password-manager)
* [Norton - Password management: Keep your passwords safer and private online](https://uk.norton.com/blog/privacy/password-management-how-to-secure-your-password)
* [Forbes - Norton Password Manager Review 2023](https://www.forbes.com/advisor/business/software/norton-password-manager-review/#:~:text=Is%20Norton%20Password%20Manager%20secure,been%20operating%20for%20several%20years.)
* [Norton - Privacy Center](https://www.nortonlifelock.com/us/en/privacy/)
* [Wikipedia - Norton Password Manager](https://en.wikipedia.org/wiki/Norton_Internet_Security)

<br>

----
<a name="passManDem"></a>
# 3. Password Manager - Demonstrate


<br>

----
<a name="message"></a>
# 4. Message - Encrypt and Decrypt
