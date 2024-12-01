# PasswordVault_Demo

# Password Vault Project - Testing Phase

## Overview

This project is an initial implementation of a **Password Vault**, designed to manage and store user credentials (websites, usernames, and passwords) in a simple and user-friendly way. The current version was created as a **starting point** to explore the basic functionality of a password management system. It **does not utilize an encryption key**, making it less secure, as its main purpose was to test and understand the workflow of such an application.

The application is built using Python with **Tkinter** for the graphical user interface (GUI) and **SQLite** for database storage.

---

## Features in This Version

1. **Master Password Setup**: 
   - Users can set a master password to access the vault.
   - The master password is stored using an MD5 hash (note: MD5 is not secure for password storage in production).
   
2. **Add Credentials**:
   - Add website, username, and password information directly into the vault.

3. **View Stored Credentials**:
   - Credentials are displayed in the vault with options to delete them.

4. **Delete Credentials**:
   - Allows users to delete entries from the vault.

---

## Key Differences From the Upcoming Version

This version was built as a **testing phase** to understand how the fundamental features of a password manager work. While functional, it has several security and usability limitations:

### 1. **No Encryption Key**
   - This version hashes the master password using MD5 but does not encrypt the stored passwords in the database. 
   - Passwords are stored as plain text in the SQLite database, which is not secure.

### 2. **Initial Prototype**:
   - The focus was on creating a basic functional application rather than ensuring robust security or advanced usability.

---

## Ongoing Improvements

The current version of the password vault is being actively improved to address previous limitations and introduce modern security features. Below are the key enhancements being implemented in the code:

### 1. **Enhanced Security with Encryption**
   - **AES Encryption**: Passwords and sensitive data are now encrypted using the AES standard via the **Fernet** encryption module.
   - **Key Derivation**: The encryption key is generated securely using the PBKDF2 (Password-Based Key Derivation Function 2) with **SHA-256** hashing, a salt, and multiple iterations to resist brute-force attacks.
   - **Salt Usage**: A static salt (`b"2444"`) is included to enhance key derivation security, with plans for more dynamic salt management in future iterations.

### 2. **Password Generation**
   - Integrated a **secure password generator** using Python's `secrets` module, which creates random, complex passwords with a customizable length, combining letters, digits, and special characters.

### 3. **Improved Database Design**
   - The SQLite database schema has been refined to include tables for:
     - **Master Password**: Stores hashed master passwords and their recovery keys.
     - **Vault**: Stores encrypted credentials (website, username, password).
     - **Master Key**: Manages the secure storage and recovery of master encryption keys.
   - Ensures credentials are stored in an encrypted format, minimizing plaintext exposure.

### 4. **Master Password Recovery**
   - Introduced a **recovery key** system:
     - Users receive a unique recovery key upon setup, which can regenerate the master encryption key in case the master password is lost.
   - The recovery key itself is hashed for secure storage in the database.

### 5. **Improved User Experience**
   - Refined **Tkinter GUI**:
     - Enhanced navigation between screens (setup, login, vault).
     - Dynamically generated forms for adding and viewing credentials.
   - Added an option to **copy recovery keys** to the clipboard for convenience.

### 6. **Transition to Modular Functions**
   - Improved code structure with reusable functions for encryption, decryption, and hashing to avoid redundancy and enhance maintainability.

---

## Features Under Development
1. **Dynamic Salt Management**
   - Incorporating unique salts for each user or session for added security during key derivation.

2. **GUI Upgrades**
   - Transitioning to modern frameworks like **PyQt** for a sleeker, more responsive interface.

3. **Credential Management Enhancements**
   - Adding features like searching and categorizing stored credentials.
   - Implementing secure password visibility toggles.

4. **Executable Packaging**
   - Converting the project into a standalone application using tools like **PyInstaller**, allowing users to run it on any platform without installing dependencies.

---

These improvements mark a significant step towards making the Password Vault more secure, functional, and user-friendly. Future iterations will continue to prioritize both security and usability to provide a robust password management solution.


---

## Acknowledgments

This version serves as the **foundation** for building a more advanced and secure password vault application. It was an essential step in understanding how password vaults work and identifying areas for improvement.

Stay tuned for the next version, where security and usability will be significantly enhanced!

---

## License

This project is licensed under the **MIT License**. You are free to use, modify, and distribute this project, provided proper attribution is given. See the [LICENSE](LICENSE) file for details.

