# Entra ID Configurations

## Status

Done — users, groups, MFA, self-service password reset, Conditional
Access, and the dynamic group are all live in the Azure subscription's
Microsoft Entra ID (Default Directory). The premium features were
unblocked on Nov 21, 2026 by a 30-day Microsoft 365 Business Premium
trial, which includes Entra ID P1. The M365 Developer Tenant (Instant
Sandbox) is not available — Microsoft now limits the free E5 developer
sandbox to Visual Studio Professional/Enterprise subscribers, partner
program members, or Premier/Unified Support customers, and a personal
account does not qualify — so this work uses the Entra ID tenant that
comes with the Azure free trial instead.

The trial is free ($0.00), expires Dec 21, 2026, and recurring billing
is Off, so it ends without charging. Two of the 25 trial licenses are assigned (admin account + Alex Rivera, 2/25); the other 23 stay unassigned.

## What This Is

Identity and access configurations in Microsoft Entra ID, practiced in
the Default Directory of the Azure free trial. This repo documents the
users, groups, MFA, password reset, Conditional Access, and dynamic
group I set up.

## Tools Used

- Microsoft Entra ID (Default Directory, in the Azure free trial)
- Azure Portal (portal.azure.com)
- Entra admin center (entra.microsoft.com)
- Microsoft 365 Business Premium trial (30 days, includes Entra ID P1)

## What I Built

### Users (5 test users, created Nov 21, 2026)

- Alex Rivera — alex.rivera@alvingonzogmail.onmicrosoft.com — IT Department
- Priya Sharma — priya.sharma@alvingonzogmail.onmicrosoft.com — IT Department
- Marcus Webb — marcus.webb@alvingonzogmail.onmicrosoft.com — Finance Department
- Sofia Chen — sofia.chen@alvingonzogmail.onmicrosoft.com — Finance Department
- David Kim — david.kim@alvingonzogmail.onmicrosoft.com — Sales Department

All are cloud-only test accounts created manually in the portal with auto-generated passwords.

Outcome: 5 test users live in the Default Directory with departments set (see the users summary).

### Groups (3 Security groups, Assigned membership)

- IT Department — members: Alex Rivera, Priya Sharma
- Finance Department — members: Marcus Webb, Sofia Chen
- Sales Department — member: David Kim

Outcome: 3 Security groups live with members assigned (see the groups summary).

### MFA

Multi-factor authentication was first enforced by Security Defaults,
which was already Enabled in this directory. To enable Conditional
Access (below), Security Defaults had to be turned off first — the
portal blocks Conditional Access while Security Defaults are on.
Turning them off auto-created 4 Microsoft-managed policies, all On:
Multifactor authentication for admins, Multifactor authentication for
all users, Multifactor authentication for Azure Management, and Block
legacy authentication. MFA protection remains, now enforced by those policies instead of Security Defaults.

Outcome: MFA is enforced for all users by the 4 Microsoft-managed policies.

### Self-service password reset (SSPR) — done Nov 21, 2026

Self-service password reset is set to All users, so any user can reset
their own password. This needed Entra ID P1, which the Business Premium trial provides.

Outcome: any user can reset their own password — SSPR set to All.

### Conditional Access — done Nov 21, 2026

Policy "Block sign-in outside US" — created and On (policy ID
bf5283ef-e843-4d60-a156-6a75c6e4c423). Scope: all users, with the admin
account excluded so the admin cannot lock itself out. Target: all
resources (all cloud apps). Condition: any network or location, with
the named location "United States" excluded. Grant: Block access. A
sign-in from outside the United States is blocked; a sign-in from
inside the US is allowed.

Outcome: sign-ins from outside the US are blocked — the policy is On.

### Dynamic group — done Nov 21, 2026

Dynamic Security group "IT Department - Dynamic" (Object ID
541633b8-38cc-4dae-bef5-2b8cfc3e23b1). Rule: user.department -eq
"IT Department". The Department attribute was set on all 5 test users
first (Alex Rivera and Priya Sharma = IT Department; Marcus Webb and
Sofia Chen = Finance Department; David Kim = Sales Department). After
the rule evaluated (about 5 minutes), membership populated with 2 members: Alex Rivera and Priya Sharma.

Outcome: the group has 2 members (Alex Rivera, Priya Sharma) — the rule works.

## Screenshots

The Azure Portal's user and group tables do not survive print-to-PDF,
so instead of portal screenshots this repo has clean summary documents
built from the data verified live in the portal on Nov 21, 2026:

- [entra-id-users-summary.pdf](entra-id-users-summary.pdf) — All users list (5 test users + owner)
- [entra-id-groups-summary.pdf](entra-id-groups-summary.pdf) — All groups list (3 groups + members)
- [entra-id-security-defaults-summary.pdf](entra-id-security-defaults-summary.pdf) — Security Defaults showing
  "Enabled (recommended)" (as it was before Conditional Access)
- [entra-id-premium-features-summary.pdf](entra-id-premium-features-summary.pdf) — SSPR, the Conditional Access
  policy, and the dynamic group, as verified after the trial unlocked
  Entra ID P1

## Why It Matters

Identity is the front door to everything in Microsoft 365 and Azure.
MFA, groups, and Conditional Access are the controls that keep accounts
safe, and they're core to the Microsoft Technology Consultant role.

## Next Steps

- The Entra ID work in the Word doc guide is complete. The remaining
  portfolio work is Intune device management and the Exchange admin
  tasks (see the intune-device-management and m365-admin-runbooks
  repos).
