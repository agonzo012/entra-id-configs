# Entra ID Configurations

## Status

Partly done — users, groups, and MFA are live in the Azure subscription's
Microsoft Entra ID (Default Directory). Conditional Access, dynamic groups,
and self-service password reset need Entra ID P1, which the free tier does
not include, so those are documented as blocked below. The M365 Developer
Tenant (Instant Sandbox) is not available — Microsoft now limits the free
E5 developer sandbox to Visual Studio Professional/Enterprise subscribers,
partner program members, or Premier/Unified Support customers, and a
personal account does not qualify — so this work uses the Entra ID tenant
that comes with the Azure free trial instead.

## What This Is

Identity and access configurations in Microsoft Entra ID, practiced in
the Default Directory of the Azure free trial. This repo documents the
users, groups, and MFA I set up, plus the premium features that are
blocked on licensing.

## Tools Used

- Microsoft Entra ID (Default Directory, in the Azure free trial)
- Azure Portal (portal.azure.com)
- Entra admin center (entra.microsoft.com)

## What I Built

### Users (5 test users, created Nov 21, 2026)

- Alex Rivera — alex.rivera@alvingonzogmail.onmicrosoft.com — IT Department
- Priya Sharma — priya.sharma@alvingonzogmail.onmicrosoft.com — IT Department
- Marcus Webb — marcus.webb@alvingonzogmail.onmicrosoft.com — Finance Department
- Sofia Chen — sofia.chen@alvingonzogmail.onmicrosoft.com — Finance Department
- David Kim — david.kim@alvingonzogmail.onmicrosoft.com — Sales Department

All are cloud-only test accounts created manually in the portal with
auto-generated passwords.

### Groups (3 Security groups, Assigned membership)

- IT Department — members: Alex Rivera, Priya Sharma
- Finance Department — members: Marcus Webb, Sofia Chen
- Sales Department — member: David Kim

### MFA (Security Defaults)

Multi-factor authentication is enforced by Security Defaults, which was
already Enabled in this directory ("Your organization is protected by
security defaults"). Security Defaults is the free-tier way to enforce
MFA for all users, including the admin account. No change was needed.

## Blocked (needs Entra ID P1)

These need a Microsoft Entra ID P1 (or P2) license, which the free tier
does not include:

- **Self-service password reset (SSPR)** — users resetting their own
  passwords requires P1. Admins can still reset a user's password.
- **Conditional Access** — a policy blocking sign-in from outside the US
  requires P1.
- **Dynamic groups** — a group that auto-adds users by a department rule
  requires P1.

## Screenshots

The Azure Portal's user and group tables do not survive print-to-PDF,
so instead of portal screenshots this repo has clean summary documents
built from the data verified live in the portal on Nov 21, 2026:

- entra-id-users-summary.pdf — All users list (5 test users + owner)
- entra-id-groups-summary.pdf — All groups list (3 groups + members)
- entra-id-security-defaults-summary.pdf — Security Defaults showing
  "Enabled (recommended)"

## Why It Matters

Identity is the front door to everything in Microsoft 365 and Azure.
MFA, groups, and Conditional Access are the controls that keep accounts
safe, and they're core to the Microsoft Technology Consultant role.

## Next Steps

- If Entra ID P1 becomes available, add SSPR, the Conditional Access
  policy (block sign-in outside the US), and the dynamic group by
  department rule, and document them here.
