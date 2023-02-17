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


## [10.3 ENCRYPTING COMMUNICATIONS CHANNELS](https://learning.oreilly.com/library/view/applied-cryptography-protocols/9781119096726/19_chap10.html#chap10-sec003)


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
