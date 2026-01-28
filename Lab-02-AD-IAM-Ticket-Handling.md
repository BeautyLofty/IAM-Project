**Lab 2: IT Support & IAM Ticket Handling (Active Directory)**

---

## Objective

Simulate real-world IT Service Desk and Identity & Access Management (IAM) scenarios using Active Directory. This lab demonstrates hands-on handling of common user account tickets, troubleshooting authentication issues, applying security policies, and documenting learning outcomes suitable for a professional IT portfolio.

---

## Environment

* Hypervisor: VirtualBox
* Virtual Machine: Windows Server (Domain Controller)
* Domain: LAB (lab.local)
* Administrator Account: LAB\Administrator
* Users Involved:

  * joejane (standard domain user)
  * [second user]
* Security Group:

  * SOCadmin
* Tools Used:

  * Server Manager
  * Active Directory Users and Computers (ADUC)
  * Group Policy Management
  * Command Prompt

---

## Ticket 1: User Cannot Log In (Password Issue)

### Issue Description

User reported inability to log in due to incorrect username or password.

### Investigation

* Verified user account exists in ADUC
* Checked account status:

  * Account disabled: No
  * Account locked: No

### Resolution

* Reset password for user **joejane**
* Provided temporary password
* Confirmed password reset confirmation

**Screenshot:** Lab2_Ticket1_PasswordReset.png

---

## Ticket 2: User Account Disabled / Access Issue

### Issue Description

User received message indicating account was disabled.

### Investigation

* Opened ADUC → User Properties
* Verified account status icon and settings

### Resolution

* Confirmed account was enabled
* No further action required

**Screenshot:** Lab2_Ticket2_AccountStatus.png

---

## Ticket 3: Group Membership / Privileged Access Request

### Issue Description

User requested elevated access via security group membership.

### Investigation

* Opened SOCadmin group properties
* Reviewed current members

### Resolution

* Added **joejane** and a second user to **SOCadmin** group
* Verified group membership

**Screenshot:** Lab2_Ticket3_SOCadminGroup.png

---

## Ticket 4: Account Lockout (Advanced IAM Scenario)

### Issue Description

User unable to authenticate after multiple failed login attempts.

### Initial Observation

* Attempts to simulate lockout failed
* Account did not lock despite repeated authentication failures

### Root Cause

No account lockout policy configured in the domain (default setting).

### Action Taken

#### Configure Account Lockout Policy

1. Opened Group Policy Management
2. Edited **Default Domain Policy**
3. Navigated to:
   Computer Configuration → Policies → Windows Settings → Security Settings → Account Policies → Account Lockout Policy
4. Configured:

   * Account lockout threshold: 3
   * Account lockout duration: 30 minutes
   * Reset account lockout counter after: 30 minutes
5. Forced policy update using:

```
gpupdate /force
```

**Screenshot:** Lab2_Ticket4_LockoutPolicy.png

---

### Simulating Lockout

* Used command:

```
runas /user:LAB\\joejane cmd
```

* Entered incorrect password multiple times
* Received confirmation:
  "The referenced account is currently locked out and may not be logged on"

### Verification

* Checked user properties in ADUC
* Confirmed **Account is locked out** checkbox enabled

**Screenshot:** Lab2_Ticket4_AccountLocked.png

---

### Resolution

* Unchecked **Account is locked out** in ADUC
* Applied changes
* User account restored

**Screenshot:** Lab2_Ticket4_AccountUnlocked.png

---

## Challenges & Troubleshooting Highlights

* Encountered System Error 53 when using `net use` due to name resolution issues
* Learned multiple methods exist to simulate authentication failures
* Understood default domain policies may not enforce security controls until configured
* Identified differences between Domain Controller login behavior and standard client machines
* Managed VM keyboard capture and focus issues during Ctrl+Alt+Del operations

---

## Lessons Learned

* IAM troubleshooting requires policy awareness, not just account checks
* Group Policy plays a critical role in enterprise security
* Account lockouts are policy-driven, not automatic
* Clear documentation is essential for IT support roles
* Real-world IT involves diagnosing both technical and configuration-related issues

---

## Skills Demonstrated

* Active Directory user and group management
* Password resets and account recovery
* Group Policy configuration
* Account lockout simulation and resolution
* Troubleshooting authentication and access issues
* Professional IT documentation

---

## Next Steps

* Lab 3: Windows Server Services & Event Viewer
* Lab 4: Client VM Join to Domain
* Lab 5: Azure AD / Microsoft Entra ID Basics

---

**Note on screenshots:**
Insert screenshots manually where indicated. Suggested filenames:

* Lab2_Ticket1_PasswordReset.png
* Lab2_Ticket2_AccountStatus.png
* Lab2_Ticket3_SOCadminGroup.png
* Lab2_Ticket4_LockoutPolicy.png
* Lab2_Ticket4_AccountLocked.png
* Lab2_Ticket4_AccountUnlocked.png
