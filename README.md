# Linux Practical 02: Enterprise User and Group Management

## Project Overview

This project demonstrates basic Linux system administration skills using Ubuntu Linux on Windows Subsystem for Linux (WSL).

The practical simulates a company environment where employees from different departments require controlled access to departmental directories.

**Role:** Junior Linux System Administrator  
**Operating System:** Ubuntu Linux (WSL)  
**Terminal:** VS Code Integrated Terminal  
**Difficulty:** Beginner to Intermediate

## 1. Project Objectives

The objectives of this practical were to:

- Create and manage Linux directories.
- Understand Linux brace expansion.
- Create departmental groups.
- Manage employee accounts.
- Assign users to departmental groups.
- Configure directory ownership.
- Apply Linux permissions using `chmod`.
- Inspect directory structures using `tree`.
- Verify group membership and directory permissions.

## 2. Company Structure

The company has three departments:

| Department | Group | Employee |
|---|---|---|
| Human Resources | company_HR | dami |
| Development | company_Development | chika |
| Finance | company_finance | simi |

## 3. Directory Structure

The following departmental directory structure was created:

```text
Company/
├── HR/
│   ├── Payroll/
│   └── Account/
├── Development/
│   ├── Project/
│   └── Demonstration/
└── Finance/
    ├── Audit/
    └── Log/
```

### Creating Multiple Directories

Linux brace expansion was used with `mkdir -p`:

```bash
mkdir -p Company/{HR/{Payroll,Account},Development/{Project,Demonstration},Finance/{Audit,Log}}
```

### Inspecting Directories

The `tree` command was used to display the directory structure.

```bash
tree Company
```

## 4. Directory Ownership

The departmental directories were assigned to the root user and their respective departmental groups.

```bash
sudo chown root:company_HR Company/HR

sudo chown root:company_Development Company/Development

sudo chown root:company_finance Company/Finance
```

## 5. Linux Permissions

The following permissions were configured:

```bash
sudo chmod 770 Company/HR

sudo chmod 750 Development

sudo chmod 740 Finance
```

### Permission Explanation

| Permission | Meaning |
|---|---|
| 770 | Owner and group have full permissions |
| 750 | Owner has full permissions; group has read and execute |
| 740 | Owner has full permissions; group has read only |

## 6. Verification

The `ls -la` command was used to inspect directory ownership and permissions.

```bash
ls -la
```

The `getent` command was used to inspect departmental group information:

```bash
getent group company_HR company_Development company_finance
```

Employee group membership was also checked using:

```bash
id dami
id chika
id simi
```

## 7. Skills Demonstrated

Through this practical, I gained experience with:

- Linux directory management.
- Linux group management.
- Linux user administration.
- File and directory ownership.
- Linux permission management.
- Brace expansion.
- Directory inspection.
- Basic Linux troubleshooting.

## 8. Lessons Learned

1. Linux is case-sensitive.
2. `mkdir -p` can create multiple nested directories.
3. `chown` changes ownership.
4. `chmod` changes permissions.
5. `ls -la` displays hidden files and detailed permission information.
6. `getent` helps retrieve group information.
7. `id` displays user and group membership.
8. Relative and absolute paths behave differently depending on the current working directory.

## 9. Further Improvements

Future improvements to this project include:

- Implementing setgid permissions.
- Testing departmental access restrictions.
- Verifying access using `sudo -u`.
- Configuring consistent group permissions.
- Completing a final system security audit.

## Conclusion

This project provided practical experience with Linux user and group administration, directory management, ownership and permissions.

It represents an important step in developing the Linux administration skills required for system administration, cloud engineering and cybersecurity.
