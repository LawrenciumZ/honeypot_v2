# AWS Account Baseline Setup

Date completed: 2026-11-18
Region: us-east-2

## Goal
Set up the account so mistakes and compromises have limited damage
before building the honeypot.

## Controls

| Control | Why I did it | How I verified it |
|---|---|---|
| MFA on root account | Root compromise means total loss | MFA shows "Assigned" in Security credentials |
| $5 monthly budget alert | Limits surprise costs from a forgotten instance | Budget visible in Billing > Budgets |
| Daily-use IAM user, root not used | Fewer chances for root credentials to be exposed | Console shows the IAM user name when signed in |
| MFA on IAM user | A stolen password alone is not enough | MFA device listed on the user |
| No active access keys | Leaked keys are a listed threat in my threat model | Access keys section is empty (stale key deleted on 2026-11-18) |

## Known tradeoff
The IAM user has AdministratorAccess. That is broader than needed
(not least privilege). I accepted this for a personal learning
account to get started. I plan to replace it with narrower
permissions once I know exactly which services I use.

## Finding: stale access key from an earlier project
- Date found: 2026-11-18
- Found while: verifying the "no access keys" control
- Details: one active key, about 259 days old, last used about
  259 days ago for CloudFront in us-east-1. It was left over from
  building my portfolio website.
- Belonged to: IAM user admin3080
- Risk: an old unused but active key can be abused if its secret
  was ever leaked
- Checks: searched the files and full history of honeypot_v2 and
  my portfolio site's repo for key IDs (nothing found)
- Action: deactivated the key, confirmed the portfolio site still
  loaded, then deleted it on 2026-11-18
- Lesson: audit existing credentials before building on an account
