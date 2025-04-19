# Hackathon Project – EuphratesTech SRE & DevOps Hackathon 2025
## Team: [Your Team Name]**Team Lead:** [Your Name]  **Repository:** https://github.com/Oladev-01/Hackathon-Python-Django  **Tech Stack:** Python, Django, PostgreSQL, Docker
---
## Overview
This project addresses real-world security and DevOps issues through deep refactoring, hardening, and design improvements. The original codebase had several critical security flaws. Over the 12-hour hackathon, our team systematically identified and resolved 9 major issues aligned with modern DevSecOps and SRE practices.
---
## Deliverables
- **Refactored Codebase:** Clean commit history and secure structure- **Deployment Files:** `Dockerfile`, `docker-compose.yml`, PostgreSQL setup- **README:** Full breakdown of issues and solutions (you’re reading it)- **4-minute Video Demo:** [Link to video demo here]- **.env Security:** Sensitive keys & configs now loaded securely
---
## Identified & Resolved Issues (Security & Design)
### 1. **Cookie Tampering – Admin Privilege Escalation**- **Issue:** Client could change `admin=0` to `admin=1` to access secret routes.- **Fix:** Replaced logic with role-checking from the server-side database session.
---
### 2. **Hardcoded Secrets in `settings.py`**- **Issue:** Secret keys and DB credentials were visible in plaintext.- **Fix:** Moved all secrets to `.env` file and loaded using `python-decouple`.
---
### 3. **PostgreSQL Credentials Not Secured**- **Issue:** DB credentials hardcoded and exposed in source files.- **Fix:** Environment variables now used to secure connection config.
---
### 4. **User-Agent Header Injection**- **Issue:** Custom headers could manipulate server behavior.- **Fix:** Sanitized `User-Agent` input and blocked non-standard values.
---
### 5. **Hardcoded Admin Credentials**- **Issue:** Admin credentials were hardcoded in the login logic.- **Fix:** Auth now checks securely against hashed database records only.
---
### 6. **Weak Password Hashing (MD5)**- **Issue:** MD5 used for password hashing, making it vulnerable to cracking.- **Fix:** Integrated `PasswordHasher` from `passlib` for secure hashing.
---
### 7. **SQL Injection Attack**- **Issue:** Raw queries were executed using unescaped user input.- **Fix:** Parameterized the queries to avoid SQL injection vectors.
---
### 8. **Ticket Allocation Design Flaw**- **Issue:** Users could bypass the 5-ticket limit via malformed requests.- **Fix:** Added strict ticket count validation before processing requests.
---
### 9. **Eval Injection (Remote Code Execution)**- **Issue:** `eval()` was used to process client input, enabling RCE.- **Fix:** Replaced `eval()` with strict input checks (e.g., `.isdigit()`).
---
## Setup Instructions
```bashgit clone https://github.com/Oladev-01/Hackathon-Python-Django.gitcd Hackathon-Python-Django
# Create virtual environmentpython3 -m venv venvsource venv/bin/activate
# Install dependenciespip install -r requirements.txt
# Set up environment variablescp .env.example .env  # Fill in your values
# Run the apppython manage.py migratepython manage.py runserver

Compliance Checklist

[x] All secrets moved to .env

[x] SQL Injection fixed

[x] No hardcoded credentials

[x] Secure password hashing implemented

[x] Admin privilege access secured

[x] No eval-based execution

[x] Domain input sanitized

[x] Secure deployment pipeline prepared

[x] GitHub commit history cleaned



---

Known Limitations

Not yet integrated with production-grade logging/monitoring tools

Rate-limiting and brute-force protections not implemented

Unit test coverage needs improvement



---

Conclusion

We applied a security-first refactoring approach to transform the codebase into a secure, stable, and production-ready system. The project reflects our understanding of DevOps, secure coding, CI/CD, and system reliability.

Let's build a more secure digital Nigeria together.


link to video presentation: https://drive.google.com/file/d/1J_ZyrKm7RQlt-9BSvTL0NgvN_ONk9as0