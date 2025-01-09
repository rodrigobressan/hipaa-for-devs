---
title: Integrity Controls
parent: Transmission Security
nav_order: 1
---

### 1. **What Are Integrity Controls?**

Integrity Controls ensure that EPHI is transmitted without being altered, tampered with, or corrupted during its journey over electronic communication channels. If the data is modified, it should be detectable by the receiving system, allowing it to flag potential security issues.

### 2. **Why It’s Important**

When transmitting sensitive health data, unauthorized modifications can pose serious risks, including:

- **Misinformation** that could lead to incorrect medical decisions.
- **Data breaches** if tampered information is sent to the wrong recipients.
- **Compromise of patient privacy** if altered data leads to unauthorized access.

### 3. **Key Requirements:**

The Integrity Controls specification has a few key points:

- **Detection of Modification**: Ensure that EPHI is not modified without detection during transmission.
- **Timely Identification**: Any modification or tampering should be easily identifiable so the sender or receiver can respond appropriately.

### 4. **Best Practices for Implementing Integrity Controls**

Here are the recommended steps to ensure integrity during transmission:

### a. **Use Secure Transmission Protocols**

Start with adopting secure transmission methods that provide built-in integrity checks. Some of the most common secure transmission protocols are:

- **HTTPS** (Hypertext Transfer Protocol Secure): Secures data over the internet using SSL/TLS encryption, which ensures that the data cannot be altered while in transit.
- **SFTP** (Secure File Transfer Protocol): A secure method for transferring files with built-in encryption and integrity checks.
- **TLS** (Transport Layer Security): Ensures that data being transmitted between systems is encrypted and not tampered with during the exchange.

These protocols automatically provide integrity controls by validating that the data being transmitted is received without modifications.

### b. **Use Message Authentication Codes (MACs)**

Message Authentication Codes (MACs) are additional security layers to verify the integrity of transmitted data. These codes work by generating a hash value (a digital fingerprint) of the message content, which is sent alongside the message. Upon receipt, the receiver computes the hash again and compares it to the sent hash. If they don’t match, the data has been altered.

For example, HMAC (Hash-based Message Authentication Code) is often used for verifying the integrity of messages.

### c. **Implement Data Checksums**

Checksums are a method of verifying data integrity by generating a calculated value based on the content of the data. After transmission, the receiving system recalculates the checksum and verifies it matches the original. This can help catch any corruption or modification during transmission.

### d. **Integrate Logging and Monitoring**

Implement logging and real-time monitoring of all data transmissions. Logs should include:

- The type of transmission (e.g., email, file transfer, API request).
- The status of the transmission.
- Any discrepancies, such as failed checksums or mismatch warnings in the integrity checks.

Regularly auditing these logs can help identify any transmission issues or potential tampering early.

### e. **Conduct Regular Risk Assessments**

Regularly assess your transmission methods, as well as how EPHI is handled within your network. Ask yourself:

- Are current integrity measures sufficient to prevent data tampering?
- Have new methods of transmission been adopted that need additional safeguards?
- What are the risks that could cause data modification during transmission, and how can these be mitigated?

By conducting regular risk analyses, you can identify new potential vulnerabilities and adapt your security practices as needed.

### 5. **Common Scenarios to Consider**

- **Email Transmission**: When EPHI is sent via email, using secure email services with built-in encryption and integrity checks (e.g., S/MIME) ensures that data isn’t altered in transit.
- **API-based Communication**: If you're using APIs to transmit EPHI, ensure that all data sent over the API is encrypted, and include MAC or checksums to validate the integrity of the data in transit.
- **Cloud-based Storage and Transfer**: When storing and transferring EPHI via cloud services (e.g., AWS), use secure file-sharing protocols, and apply checksums to confirm data integrity before and after transmission.

### 6. **Questions to Ask for Compliance**

To ensure that your system complies with the Integrity Controls standard, consider the following questions:

- **What security measures are currently used to protect EPHI during transmission?**
- **Has the risk analysis identified scenarios that could lead to unauthorized modification of EPHI?**
- **What security measures can be implemented to protect EPHI from unauthorized access or modification during transmission?**
- **Do we have a monitoring system in place to detect any modifications during transmission?**