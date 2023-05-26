# Research

This contains research materials and information related to Safe Exam Browser (SEB).

## Safe Exam Browser (SEB)

Safe Exam Browser is a software that allows students to securely take exams on their own computers. It is designed to prevent examinees from altering the exam configuration and to keep certain details of the exam configuration confidential, thus hindering any attempts to manipulate the exam settings.

SEB uses an encrypted configuration file format with the extension .seb to store exam configurations. The encryption is implemented to ensure that examinees cannot modify the exam configuration and to safeguard the secrecy of certain exam details. The encryption is designed to follow current cryptography standards and should be as secure as possible.

The exam settings are defined in an XML structure with key/value pairs. The key names in the configuration file are self-explanatory and avoid abbreviations. The goal is to use the same .seb files across different platforms, including Windows, Mac OS X, iOS, Linux, and Android. While aiming for platform-independent compatibility, some settings may have different functionalities or may not be available on certain platforms. In such cases, a compatible way of configuring clients is found by using a general meta key for enabling/disabling a specific functionality and individual detail keys per platform for specific configuration details.

SEB supports two encryption/decryption methods:

1. **Password-Based Encryption**: When opening a .seb file, the password used to encrypt the file needs to be entered. This method ensures that the encrypted data (cyphertext) and the key (secret) are kept separate, as long as the exam administrator chooses a strong password and keeps it confidential until the exam starts. This method is ideal for non-centrally managed student computers.

2. **Encryption with Certificate/Key**: For encrypting .seb files, a cryptographic key combined with an X.509 certificate is used. This key is deployed to the exam client computers before the exams and securely stored in the Windows Certificate Store or the OS X Keychain. On centrally managed computers where users/examinees don't have administrator access, the key is separated from the cyphertext. This method enhances security and avoids the use of a general key stored inside the SEB application code, which could be extracted and potentially compromise the entire SEB installation worldwide. Each institution using SEB can generate their own certificates/keys and replace them as needed. Encryption with a certificate/key can be combined with password encryption for additional security in specific exams.

For more information about the encrypted SEB config file format, please refer to the [SEB File Format documentation](https://safeexambrowser.org/developer/seb-file-format.html).