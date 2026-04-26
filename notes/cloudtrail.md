# CloudTrail

## Observations
- Event history was available before I created a trail.
- Event history showed management activity tied to account setup and later lab actions.
- CloudTrail captured sign-in and IAM-related activity.
- CloudTrail also captured S3 bucket changes made during the investigation phase.
- Event history is useful evidence, but it is not the same thing as a trail.

## Events I saw
- GetSigninToken
- UserAuthentication
- CredentialVerification
- CredentialChallenge
- AttachRolePolicy
- CreateBucket
- PutBucketEncryption
- PutBucketVersioning
- GetBucketVersioning
- PutBucketPolicy

## What these tell me
- CloudTrail records what happened in the account.
- It can show who performed an action, when it happened, and whether it was a read or write event.
- `GetBucketVersioning` checked status, while `PutBucketVersioning` made the actual change.
- `managementEvent = true` meant the event was a management/control-plane event.
- `readOnly = false` meant the event was a write/change action.
- Request parameters helped confirm what actually changed.

## Why it mattered in this lab
CloudTrail became the main evidence source during the investigation phase. It helped confirm:
- bucket creation activity
- bucket versioning changes
- denied bucket policy attempts
- IAM user creation
- read-only versus write activity

## What clicked
CloudTrail is the main source of proof for what actually happened in the AWS account.
