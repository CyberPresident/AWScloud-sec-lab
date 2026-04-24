# CloudTrail

## Observations
- Event history was already available before I created a trail.
- Event history showed recent management activity tied to my account setup.
- My sign-in flow appeared in CloudTrail.
- IAM-related setup actions also appeared in the event list.
- Event history is useful evidence, but it is not the same thing as a trail.

## Events I saw
- ConsoleLogin
- GetSigninToken
- Authenticate
- UserAuthentication
- CredentialVerification
- CredentialChallenge
- CreateRole
- AttachRolePolicy

## What these tell me
- CloudTrail records actions taken in the account.
- It can show authentication and sign-in related activity.
- It can show IAM setup and permission-related changes.
- CloudTrail helps prove that actions actually happened.
- Event history helps with visibility, but a trail is needed for ongoing log delivery.

## What I need to learn
- management events vs data events
- what changes once a trail is created
- why multi-Region logging matters
- why log file validation matters
- how CloudTrail supports detection and investigations
