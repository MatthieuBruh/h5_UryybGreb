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

<br>

----
<a name="passManEx"></a>
# 2. Password Manager - Explain


<br>

----
<a name="passManDem"></a>
# 3. Password Manager - Demonstrate


<br>

----
<a name="message"></a>
# 4. Message - Encrypt and Decrypt
