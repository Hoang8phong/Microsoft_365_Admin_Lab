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


## Screenshots
- I will update soon
---

## Skills Practiced
- MIcrosoft 365 Administration
- DNS configuration (MX, SPF, CNAME)
- Exchange Online mail flow
- Helpdesk simulation
- Office 365 E5 licensing
- Shared mailbox & delegation
- Basic mail security & phising detection
- Enforce MFA for all user account
- Implemented self-service recovery
- Monitored and audited user activity
---

## Notes
This project is for educational purposes using the Microsoft 365 Enterprise E5 (trial). It simulates enterprise-scale IT admin tasks and is not used for commercial purposes.
