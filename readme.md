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
## [10. Using Algorithms](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/19_chap10.html#chap10)
* You can have a very secure system, if you have a component that is less secure, it determinate you security level.
* You have to secure everything in a system (protocols, encryption keys, etc.)
* In cybersecurity, you have to think of everything. One omission and it can be a flaw.
* The security designer has to think of everything. However, the attacker can only think to one flaw.
* In cybersecurity, there is not only the encryption.
* The aim is to make the crime more difficult.
* Successful attacks against cryptography is generally due to another thing than a bad cryptography algorithm.
* Most of security failures are related to a bad or wrong implementation.

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
To start using [Norton Password Manager](https://my.norton.com/extspa/passwordmanager?inid=nortoncom-overview_card22_mynorton), you have to create an account. At the same time, you can install the chrome web extensions and the mobile application.
To summarize the step to get started with NPM, you have to: 
1. Install the chrome extension.
2. Create a Norton account from the NPM extension.
3. Create a vault, it will be your password manager.
4. Create a strong and unique password that you can easily remember for your vault.
5. Recommended: Add two-factor authentication with the mobile application.
If you need help to create your account, you use the [Norton support](https://support.norton.com/sp/en/us/home/current/solutions/v54500320#:~:text=Click%20Norton%20Password%20Manager%20on,details%2C%20and%20click%20Create%20Account.).

After having created and set up your vault, you can start to use NPM.
Firstly, you have to open the Norton Password Manager extension on your browser. <br>
Secondly, you can use the yellow plus button to add a new login credentials. <br>

<p align="center"> <img alt="Create a new login" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/newLoginCredentials.png"> </p>

<p align="center"><i>During the whole demonstration my Norton Password Manager is in French. I can't change the default language, so I will translate for you. At the same time, you can learn French if you want! :smile:</i></p>


As you can see, you can enter a title under the field "civilité".
You can add an URL, so that NPM will be able to do automatic filling.
You can also use the notes field to enter other information.
Then, you can enter the username (field: "nom d'utilisateur") and the password (field: "mot de passe"). You can use the right button of the password field to generate a password as below.

<p align="center"> <img alt="Generate password" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/generatePassword.png"> </p>

When you want to generate a password, you can choose the length ("Longueur du mot de passe"), you can choose to have letters ("Lettres"), upper and lower case ("Casse mixte"), numbers ("Chiffres"), punctuation ("Ponctuation").<br>
Depending of your choice, the password reliability can change. It corresponds to the field: "Fiabilité".<br>
To use the generate password, you can click again on the yellow button ("Utiliser le mot de passe").

After having saved your credentials on the Norton Password Manager, you can go to the site you want to connect to. Let's take a random Haaga-Helia service that require authentication. On the authentication page of Haaga-Helia, I will automatically have the Norton Password Manager field. I only need to click on the popup to enter my credentials.

<p align="center"> <img alt="Haaga-Helia example" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/haaga-Helia.png"> </p>


Another interesting feature of the Norton Password Manager is the dashboard. You can easily see if your passwords are strong enough, unique, or if you have to change it because it has not been changed for a while. From this dashboard, it is also possible to change "automatically" your password. It means that NPM try to change the password on your password manager and on the website concerned. However, I don't recommend you to use it for the moment, because it does not really work properly.

<p align="center"> <img alt="Norton dashboard" src="https://static.safetydetectives.com/wp-content/uploads/2019/05/Norton-Password-Manager-Review-1.png.webp"> </p>

As said before, NPM is also available as a mobile application. It is the same concept as on your computer.

## Sources
* [Support Norton - Create Norton Password Manager cloud vault](https://support.norton.com/sp/en/us/home/current/solutions/v54500320#:~:text=Click%20Norton%20Password%20Manager%20on,details%2C%20and%20click%20Create%20Account.)
* [SafetyDetectives - Norton Password Manager Review 2023 — Is It 100% Secure?](https://www.safetydetectives.com/best-password-managers/norton-password-manager/)

<br>

----
<a name="message"></a>
# 4. Message - Encrypt and Decrypt
For this exercise, I will take the well-known example of Alice wanting to send a message to Bob. I only renamed Bob as Bobby.

As long as you are working on a Linux distro (or others operating systems), it is important to regularly update your components. In my case, I try to do at least one time every two weeks and also before I install a new component. To update my components, I wrote the following commands:

    $ sudo apt-get update
    $ sudo apt-get upgrade

After that, I am now ready to install GPG with the following command:

    $ sudo apt-get install gnupg
    
For the needs of the exercise, I created a directory named message, and I used it during the whole exercise.

    $ mkdir message
    $ cd message

Firstly, I had to generate a key pair for Alice. To generate a key with GPG, I used the command:

    $ gpg --gen-key
    # GPG asked me three information:
    #   - "Real name": Alice
    #   - "Email": alice@haaga-helia.fi
    #   - and a password

Secondly, I also needed a key pair for Bob. So, I used the same command as for Alice, but I changed the real name as Bobby, the email as bobby@haaga-helia.fi, and I created a new password.

I can now see all the keys I created with the command:

    $ gpg --list-keys

Here is the result:

<p align="center"> <img alt="My keys" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/gpgListKeys.PNG"> </p>
<p align="center"><i>As you can see, I have Alice and Bobby keys. Matthieu's key was test I did few days ago for myself.</i></p>

Now, Bobby is able to export his public key in a file named: bobby_public_key.asc. By using the command:

    $ gpg --armor --export Bobby > bobby_public_key.asc

After exporting his key, Bobby can send it to Alice. Then, Alice will import Bobby's public key with the file given by Bobby and the command:

    $ gpg --import bobby_public_key.asc

In the case of my scenario, I didn't have to do this two previous steps. This is because I generated the key for Alice and Bobby, so Bobby's key is already "imported".

Now, Alice can write her message for Bobby in a file named mesForBobby.txt. She used the command:

    $ nano mesForBobby.txt
    # She wrote a secret message in it!

Before sending the file that contains the secret message, she needed to encrypt it with the command:

    $ gpg --output mesForBobbyEnc.gpg --encrypt --recipient bobby@haaga-helia.fi mesForBobby.txt 
    # --output: specify the name of the encrypted file.
    # --recipient: specify with who's public key the message will be encrypted.
    # mesForBobby.txt: the file that will be encrypted.

She got the following result:

<p align="center"> <img alt="Encrypted file" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/encryptedMessage.PNG"> </p>
<p align="center"><i>As you can see, the file is now encrypted and unreadable.</i></p>

She is now able to send the file to Bobby. She sent it and Bobby received it.
To read the file, Bobby has to decrypt the file. So, I will use his private key and the command:

    $ gpg --output decryptedMessage --decrypt mesForBobbyEnc.gpg
    # --output: specify the name of the file where the decrypted message will be saved.
    # --decrypt: specify which file is going to be decrypted
    # This command will require a password, it is the password of Bobby's private key.

After the decryption, we will have the following message:

<p align="center"> <img alt="Decryption message" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/decryption.PNG"> </p>

Finally, Bobby can read the file by using the cat command:

    $ cat decryptedMessage

The secret message from Alice to Bob is:

<p align="center"> <img alt="Final message" src="https://github.com/MatthieuBruh/h5_UryybGreb/blob/main/screenshots/decryptedMessage.PNG"> </p>

## Sources
* [Opengenus - Encryption and decryption with gpg](https://iq.opengenus.org/encryption-and-decryption-with-gpg/)
* [Tutonics - GPG Encryption Guide - Part 1](https://tutonics.com/2012/11/gpg-encryption-guide-part-1.html)
* [GNUPG - Encrypting and decrypting documents](https://www.gnupg.org/gph/en/manual/x110.html)
