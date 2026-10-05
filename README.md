# SIEM--Windows-User-Account-Creation-Detection
Investigation --- Windows User Account Creation Detection



**Windows User Account Creation Detection — Wazuh**

Objective

Detect and investigate the creation or enabling of a Windows user account using Wazuh.

Test Activity

A temporary local Windows account named SOC-TestUser was created on the Windows 11 endpoint.

New-LocalUser -Name "SOC-TestUser" -Password (Read-Host -AsSecureString "Password")

Wazuh Detection

* Rule ID:                       60109
* Level:                         0
* Event ID:                      4722
* Description:                   User account enabled or created
* Target Account:                SOC-TestUser
* MITRE ATT&CK:                  T1098

Investigation

The alert was correlated with the account-creation activity performed during the controlled SOC lab.

The target account was a temporary test account created intentionally for security monitoring validation.

SOC Workflow

Account Creation
      ↓
Windows Security Event
      ↓
Wazuh Detection
      ↓
Alert Triage
      ↓
Identify Target Account
      ↓
Determine Legitimate/Suspicious Activity
      ↓
Remove Test Account

Key Learning

Account creation is an important identity-security event because unauthorized accounts can provide persistent access to a system. SIEM monitoring can help analysts identify and investigate unexpected account creation.

Result: Wazuh successfully detected the controlled account-creation activity.
