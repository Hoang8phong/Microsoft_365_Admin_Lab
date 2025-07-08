# Microsoft_365_Admin_Lab - Domain: `Miku39.it.com`

This lab simulates a real-world Microsoft 365 environment where I take full control of a domain, confirgue DNS, provision users, enforce policies, and simulate enterprise collaboration. Built entirely from scratch for learning and skill-building in IT support, System Admin, and IT Helpdesk.
---

## Lab Objectives

- Connect a custom domain to Microsoft 365 (DNS & email)
- Confirgue users, shared mailboxes, distribution lists
- Practice mail flow policies, security filters, and mailbox delegation
- Simulate a small business structure with realistic roles
---

## 1.: Domain + Microsoft 365 Setup
- Domain purchased: `Miku39.it.com` (via Namecheap)
- DNS records configured: MX, SPF, CNAME, TXT
- Microsoft 365 tenant: Microsoft Enterprise 365 E5 (no Teams) (trial)

DNS verification completed via TXT record
Email flow tested: Gmail test user <-> admin@Miku39.it.com
---

## 2: User & Mailbox Provisioning

Created realistic uisers to simulate orgnaization structure:

| Display Name     | Email                          | Role                   |
|------------------|--------------------------------|------------------------|
| Admin Miku       | admin@miku39.it.com            | Global Admin           |
| Vu Hoang         | vu.hoang39@miku39.it.com       | IT Admin               |
| Brian Hoang      | intern01.brian@miku39.it.com   | Intern                 |
| Ashley Hoang     | marketing.ashley@miku39.it.com | Marketing              |
| Jenna Nguyen     | ceo.jenna@miku39.it.com        | CEO                    |
| Kiel             | intern02.kiel@miku39.it.com    | Intern                 |

- All users licensed (Office 365 E5, no Teams)
---

## 3: Shared Mailbox + Groups

### Created Shared Mailbox + Groups
- **Email**: `support@Miku39.it.com`
- **Purpose**: Simulate an IT Helpdesk support inbox
- **Access granted to**: `Intern01.Brian@Miku39.it.com`, `Admin.Miku@miku39.it.com`

- Tested sending/receiving as `support@` from Outlook Web
- Shared mailbox added manually via "Open another mailbox"
---

### Distribution List (Group Email):
- `staff@Miku39.it.com` --> forwards to all users
- Simulated internal annoucements/team email
---

## 4: Mail Flow & Security Policies (Exchange)
- Auto-forward: Forwarded `Intern01.Brian`, `admin@miku39.it.com` email to ecternal Gmail
- Block EXE Attachments: Rejected `.exe` files with error message
- Phising Simulation: Flagged "urgent payment" keywords with warning banner

- All rules created in `Exchanged Admin Center > Mail Flow > Rules`
---

##  5: Identity & Access Management (Microsoft Entra)
This phase focused on secureing user identities, simulating real-world IAM (Identity and Access Management) openration inside Microsoft Entra

### Multi-Factor Authentication (MFA)
- All user were asked to use Authenticator App when first log in. However, if not
- Use Require re-register multifactor authentication and allow
- ![2  require re-register MFA](https://github.com/user-attachments/assets/7e9a8d1f-03f9-4463-a12c-8e7c666ff48d)
- Tested re-authentication using Google Authenticator
- ![4  MFA success](https://github.com/user-attachments/assets/ed9e269a-47c4-4d80-b6f3-d5dc6794cffd)
- Account `Intern03.Kiet@Miku39.it.com` is enabled
- ![5  enable MFA completre](https://github.com/user-attachments/assets/6c968efe-7c65-4ee2-a972-d5811767d27f)

**What I learned**
- How MFA protects against password-only attacks
- How to enforce secure authentication in Microsoft 365
- How MFA apears in audit logs and sign-in logs

### Group-Based Licensing 
- Created group: `Licensed Intenrns`
- ![11  create group](https://github.com/user-attachments/assets/06438484-d564-49c1-89c8-be4c9afa3d68)
- Assigned Microsoft 365 E5 Developer licened to the group
- Add `Intern01.Brian`, `Intern02.Kiel` and `Intern03.Kiet` as members
- Verified automatic license assignment via group membership
- ![12  assign Linced intern](https://github.com/user-attachments/assets/34921e1c-1ca8-4774-b209-1e88a2ffef53)

**What I learned**
- How to automate license provisioning at scale
- How to reduce admin overhead using froup-based access

### Self-Service Password Reset
- Enabled SSPR for all users
- ![7 sspr](https://github.com/user-attachments/assets/08f70bb9-4bbf-4b60-ad3f-9b6a80c15ff8)
- Tested password reset
- ![8  forgot passwored](https://github.com/user-attachments/assets/514e7401-d83c-4093-b096-5f7cd90566ce)
- ![9  reset passwords](https://github.com/user-attachments/assets/890f42ad-aadf-43cd-89ce-5a58096cb389)
- Confirmed successfull
- ![10  notofication](https://github.com/user-attachments/assets/eb57ab92-a1e7-462b-b25d-712031da73ba)

**What I learned**
- How users recover accounts without admin support
- Why fallback authentication methods are essentials
- How it help reduce Helpdesk workload

### Logs & Monitoring
- Navigated to **Sign-in logs**
  - Filtered by failure, client app, location
  - Identified login attempts by IP, device, country
- Used **Audit-logs** to conmfirmed
  - Group membership change
  - Password reset initiation
  - User management

**What I learned**
- How to monitor identity-related events and incidents
- How to audit changes to user or group configuration
- How to trace security incidents using native Entra tools
---

## 6: Assign Custom Admin Role

### Objective: 
Simulate **role-based access control** by assigning it to Admin Miku user.
- Select user and assgin role `Password Administrator` that can reset password for non-administrator and administrator to `Admin.Miku@Miku39.it.com`
![2 assigned role](https://github.com/user-attachments/assets/d215c5a0-eb2f-4fce-836c-d1f7d050d628)

### Test Results:
- User can reset anothe user's password with high privilege
![3 reset passord for Intenrn01 Brian](https://github.com/user-attachments/assets/98a6ddd4-0d43-48c3-a55f-04aefb8ab3fd)

- Other user that didn't have that role cannot reset password
![4  another account with no role](https://github.com/user-attachments/assets/3a7eea3c-0936-47fd-9967-21b27d64e516)

### What I learn:
- Implement **Least privilege** access
- Creating and testing **Custom roles in Entra**
- Realistic simulation
---

## 7: Confirgue DLP Policy for Sensitive Info

### Objective:
Block and warn user about email and file sharing that contain **financial data**, such as credit card number, ..., from being sent outside the organization

- Create a DLP policy using Microsoft Purview
- Used the "Australia Financial data" template
- Enabled monitoring on:
  - Exchange Email
  - Sharepoint site
  - OneDrive account
  - Teams chat and channel messages
  - Devices
  - Microsoft Defender for Cloud Apps
  - On-premiese repositories
- Action: Warn user and block email
![6  finish set up policies](https://github.com/user-attachments/assets/92b31c59-eff2-4c1b-b7de-1e0f85cfa949)


### Test Results:
- Email contaning test credit cxard numbers sent to test Gmail account --> was warn and block
![7  make a test to send fake credit card number to gmail com](https://github.com/user-attachments/assets/ea25554f-741d-441f-862c-4bfe7173c4ac)
![recieve warning from microsoft outllook](https://github.com/user-attachments/assets/92c4e5ee-6f08-4786-9cda-6202cb808d6d)
- Aleart was sent to admin mailbox

### What I learned
- How Microsoft detects **sensitive info types**
- Creating **compliance policies**
- Real-world application of **data governance and insider threat prevention**
---

## 8.Safe Links and Safe Attachments Protection

### Objective:
Protect users from phishing emails and malicious file attachments using **Microsoft Defender for Office 365**.

#### Safe Links Policy
- Enabled URL scanning in emails, Teams, OneDrive, and Office docs
- Disabled user override for malicious links
![create safe link policy](https://github.com/user-attachments/assets/97d69ca0-5294-46a4-9a3a-5d7b40509342)

#### Safe Attachments Policy
- Enabled sandboxing with **Dynamic Delivery**
- Applied to all users
![Create safe attachment](https://github.com/user-attachments/assets/63d45ade-1fc3-4f91-ad20-5203e64db859)

### Test Results:
- Links in external emails were rewritten and scanned
- Attachments were delayed before delivery for scanning
- Unsafe links triggered Defender warnings

### What I Learned:
- How Safe Links protect against **phishing** and **malware**
- How Safe Attachments sandbox files before delivery
- This mirrors **email protection controls used by real SOC teams**
---

## Screenshots
- I will update soon
---

## Skills Practiced
- Microsoft 365 Administration
- DNS configuration (MX, SPF, CNAME)
- Exchange Online mail flow
- Helpdesk simulation
- Office 365 E5 licensing
- Shared mailbox & delegation
- Basic mail security & phising detection
- Enforce MFA for all user account
- Implemented self-service recovery
- Monitored and audited user activity
- Microsoft Entra ID
- Role-Based Access Control in Microsoft 365
- Policy testing and validation
- Realistic simulation of enterprise security controls
---

## Notes
This project is for educational purposes using the Microsoft 365 Enterprise E5 (trial). It simulates enterprise-scale IT admin tasks and is not used for commercial purposes.
