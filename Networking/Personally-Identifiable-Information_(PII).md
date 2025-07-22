# 🔐 Personally-Identifiable-Information (PII)

**Personally Identifiable Information (PII)** refers to any data that can be used to **identify**, **contact**, or **locate** an individual — either directly or indirectly.

---

## 📄 Common Examples of PII

| **Type**        | **Examples**                                                                 |
|------------------|------------------------------------------------------------------------------|
| **Direct PII**   | Full name, Social Security Number (SSN), Passport number, etc.              |
| **Indirect PII** | Date of birth, gender, ZIP code, IP address, job title, etc.                |
| **Sensitive PII**| Biometric data, [health records](#), financial info, login credentials      |

---

## 🔐 Sensitive vs Non-Sensitive PII

| **Category**       | **Description**                                                                 |
|--------------------|----------------------------------------------------------------------------------|
| **Sensitive PII**  | Requires extra protection due to potential for harm if disclosed (e.g., SSN, bank info) |
| **Non-Sensitive**  | Publicly available info (e.g., name, workplace) unless combined with other data |

---

## 💥 Risks of PII Exposure

- 🕵️‍ Identity theft  
- 💳 Fraud and scams  
- 💢 Reputation damage  
- ⚖️ Legal and compliance violations *(e.g., GDPR, HIPAA, CCPA)*

---

## 📜 PII in Compliance & Regulations

| **Regulation** | **Region / Sector**    | **PII Protection Mandate**                                                   |
|----------------|------------------------|------------------------------------------------------------------------------|
| **GDPR**       | EU                     | Defines PII as *Personal Data*; requires consent, rights                     |
| **CCPA**       | California, USA        | Defines "personal information" broadly                                       |
| **HIPAA**      | US Healthcare          | Protects health-related PII (PHI)                                            |
| **PCI-DSS**    | Global (Payments)      | Protects credit card data, linked to identity                                |

---

## 🛡️ PII Protection Best Practices

- 🔐 Use **encryption** for storage and transmission  
- 🧹 Apply **data minimization** (only collect what’s necessary)  
- 🗑️ Perform **regular data purging**  
- ❌ Disable **auto-log** of sensitive fields (e.g., passwords, tokens)  
- 📋 Implement **access control & auditing**
