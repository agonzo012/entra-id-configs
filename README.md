# Entra ID Configurations

## What This Is

Identity and access configurations in Microsoft Entra ID, practiced in
the free Microsoft 365 Developer Tenant (Instant Sandbox). This repo
documents the users, groups, MFA, self-service password reset, Conditional
Access, and dynamic groups I set up.

## Tools Used

- Microsoft Entra ID (in the M365 Developer Tenant)
- Microsoft 365 admin center (admin.microsoft.com)
- Entra admin center (entra.microsoft.com)

## What I'm Building

- **Users and groups** — create 5 users and 3 groups manually in Entra ID
- **MFA and SSPR** — set up multi-factor authentication and self-service
  password reset
- **Conditional Access** — a policy that blocks sign-in from outside the US
- **Dynamic groups** — a group that auto-adds users by a department rule

## Status

In progress — building in the M365 Developer Tenant. Each configuration
will be documented here with screenshots as it's completed.

## Why It Matters

Identity is the front door to everything in Microsoft 365 and Azure.
Conditional Access, MFA, and SSPR are the controls that keep accounts
safe, and they're core to the Microsoft Technology Consultant role.

## Next Steps

- Finish the M365 Developer Tenant setup (Instant Sandbox)
- Create the 5 users and 3 groups
- Turn on MFA and SSPR, then build the Conditional Access policy
