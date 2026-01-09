# Time-Based Two-Factor File Protection Framework

**Time-Based Two-Factor File Protection Framework** is a Linux-based security project that enforces **two-factor authentication (2FA)** for file encryption and decryption using **Time-Based One-Time Passwords (TOTP)** and **AES-256 encryption**.

The system ensures that access to protected files requires both a valid cryptographic key and a time-synchronized one-time password.

TOTP Authentication | AES-256 Encryption | Linux Security

---

## Overview

This project was built to:
- Understand practical implementation of TOTP (RFC 6238)
- Apply time-based access control to file operations
- Combine authentication and encryption at the system level
- Study the impact of time synchronization on security mechanisms

This is an **educational project** and not a production-grade security solution.

---

## Tech Stack

- Bash (Shell Scripting)
- OpenSSL (AES-256 + PBKDF2)
- oathtool (TOTP generation)
- NTP / systemd-timesyncd (time synchronization)
- Linux file permissions

---

## Project Structure

```
root
│
├── enc_dec.sh # Encryption / decryption script
├── .enc.key # Encryption key
├── .totp.secret # TOTP shared secret
└── README.md
```



---

## How It Works

1. User runs the script in encrypt or decrypt mode
2. User is prompted for a TOTP code
3. The system validates the OTP against the current time window
4. If valid, AES-256 encryption or decryption is performed
5. Invalid authentication immediately terminates the operation

---

## Usage

```bash
chmod +x enc_dec.sh

./enc_dec.sh enc file.txt
./enc_dec.sh dec file.txt.enc
