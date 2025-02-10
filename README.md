# Managing Password Security Project

## Objective

This project focuses on managing password security within an Active Directory domain. The main goal is to demonstrate various techniques used in password cracking and security assessments, followed by the implementation of improved password policies. The project includes exercises using password spraying, dictionary attacks, brute force attacks, and password policy configuration, all aimed at strengthening the security of user accounts.

---

## Key Exercises and Concepts

### 1. **Password Spraying Attack**
   - **Objective**: Use tools like **Hydra** to perform a password spraying attack across a list of usernames and potential passwords.
   - **Goal**: Test how weak password practices (like using common passwords) make accounts vulnerable to attacks.
   - **Outcome**: Discover weak passwords and implement stronger password policies.

### 2. **Brute Force Password Cracking with John the Ripper**
   - **Objective**: Utilize **John the Ripper (JtR)** to perform a brute-force attack on password hashes.
   - **Goal**: Demonstrate the effectiveness of brute force methods against simple passwords and the computational effort required for complex ones.
   - **Outcome**: Identify cracked passwords and enforce stronger password policies.

### 3. **Dictionary Attack**
   - **Objective**: Use **John the Ripper** to perform a dictionary-based attack against password hashes.
   - **Goal**: Crack passwords based on common dictionary entries.
   - **Outcome**: Understand how dictionary attacks can break weak passwords, and how to avoid them through better password selection.

### 4. **Configuring Password Policies**
   - **Objective**: Based on the findings from previous attacks, configure a **password policy** for the domain to improve security.
   - **Goal**: Implement stronger password complexity and lockout policies in the **Structureality domain**.
   - **Outcome**: Enforce stricter password policies that adhere to best practices like length, complexity, and expiration requirements.

---

## Technologies and Tools Used

- **Kali Linux**: A Linux distribution used for penetration testing and ethical hacking.
- **John the Ripper**: A tool used for cracking passwords through dictionary and brute-force attacks.
- **Hydra**: A tool for performing password spraying and brute force attacks on network services.
- **PowerShell**: Used for managing and configuring password policies within the Active Directory environment.
- **Active Directory**: The directory service used to manage user accounts, group policies, and security settings.

---

## Setting Up the Project

### 1. **Clone the Repository**

To begin, clone the repository to your local machine using the following command:

```bash
git clone https://github.com/CoderBlee/Managing-Password-Security.git
```

### 2. **Prerequisites**

Ensure you have the following tools installed:
- **Kali Linux** or a similar penetration testing distribution.
- **John the Ripper** and **Hydra** for password cracking and brute force operations.
- **PowerShell** (on Windows) or an appropriate environment to run PowerShell commands for AD management.
- **Active Directory** environment to configure the domain password policy.

### 3. **Running the Attacks**

For each attack, follow the respective folder instructions:

1. **Password Spraying Attack**:
   - Run the **hydra-wizard** command in your terminal to initiate the attack against the target system using a list of potential passwords.

2. **Brute Force Cracking**:
   - Use **John the Ripper** to run the brute force cracking using the provided password hash file.

3. **Dictionary Attack**:
   - Execute the dictionary-based attack with **John the Ripper** using the xato-net-10-million-passwords.txt wordlist.

4. **Password Policy Configuration**:
   - Use **PowerShell** to modify Active Directory’s password policy. Apply the changes to strengthen the password requirements and lockout settings.

---

## Password Policy Configuration

Here are the configurations applied to the **Structureality domain** for a stronger password policy:

| Key                        | Value         |
|----------------------------|---------------|
| LockoutObservationWindow    | 00:15:00      |
| LockoutDuration             | 00:15:00      |
| LockoutThreshold            | 3             |
| MaxPasswordAge              | 365           |
| MinPasswordAge              | 3             |
| MinPasswordLength           | 12            |

These changes aim to:
- Implement a **lockout policy** after 3 failed attempts.
- Enforce a **minimum password length of 12 characters**.
- Set a **maximum password age** of 365 days to ensure password rotation.

---

## Best Practices and Recommendations

- **Encourage Stronger Passwords**: Users should be trained to create longer and more complex passwords to mitigate the risks of password cracking.
- **Implement Multi-factor Authentication (MFA)**: Combine password policies with MFA to enhance security further.
- **Periodic Security Audits**: Regularly audit user accounts for weak or reused passwords, ensuring compliance with security best practices.

---

## License

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details.

---