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

## 2.: User & Mailbox Provisioning

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

## 3.: Shared Mailbox + Groups

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

## 4.: Mail Flow & Security Policies (Exchange)
- Auto-forward: Forwarded `Intern01.Brian`, `admin@miku39.it.com` email to ecternal Gmail
- Block EXE Attachments: Rejected `.exe` files with error message
- Phising Simulation: Flagged "urgent payment" keywords with warning banner

- All rules created in `Exchanged Admin Center > Mail Flow > Rules`
---

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
---

## Notes
This project is for educational purposes using the Microsoft 365 Enterprise E5 (trial). It simulates enterprise-scale IT admin tasks and is not used for commercial purposes.
