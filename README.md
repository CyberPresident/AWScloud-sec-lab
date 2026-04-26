# AWS Cloud Security Lab

## Overview
This project documents a hands-on AWS security lab built in one environment and expanded in phases.

The goal was to move past basic setup and understand how AWS security controls work across four layers:

- **Foundation**: secure the account and enable core visibility and detection
- **Investigation**: use CloudTrail and GuardDuty to trace what happened
- **Hardening**: reduce risk by limiting access and avoiding unnecessary root usage
- **Response**: build a real event like workflow from GuardDuty to EventBridge to Lambda

## Services Used
- IAM Identity Center
- IAM
- CloudTrail
- GuardDuty
- Amazon S3
- AWS Budgets
- CloudWatch Logs
- Amazon EventBridge
- AWS Lambda

---

## Phase 1 - Foundation

### What I learned
- CloudTrail provides account activity visibility and evidence
- GuardDuty provides interpreted security findings, not raw logs
- S3 Block Public Access prevents risky storage exposure
- Root should not be used for normal day-to-day work

---

## Phase 2 - Investigation

### What I investigated
- `CreateBucket`
- `PutBucketEncryption`
- `PutBucketVersioning`
- `PutBucketPolicy` with `AccessDenied`
- `CreateUser`
- GuardDuty root credential usage finding

### Key investigation takeaways
- `GetBucketVersioning` checked status, but `PutBucketVersioning` was the real write/change event
- `managementEvent = true` showed a management/control-plane event
- `readOnly = false` showed a write action
- CloudTrail request parameters helped confirm what actually changed
- GuardDuty count values represented repeated occurrences tied to the same finding pattern, not the total number of findings in the console
- GuardDuty findings became more useful when tied back to CloudTrail evidence

---

## Phase 3 - Hardening

### What I changed
- Stopped using root for normal work
- Switched to IAM Identity Center as the normal access path
- Enforced always-on MFA for the Identity Center login
- Deleted a temporary IAM test user after investigation
- Created a second lower-privilege access lane using `ReadOnlyAccess`

### What I proved
- The read-only lane could view services like CloudTrail and S3
- The read-only lane could not successfully save security configuration changes
- This reduced the need to use full admin access for every action

### Hardening takeaway
This phase reduced blast radius by separating:
- **Admin access** for changes
- **Read-only access** for review and investigation

---

## Phase 4 - Response

### What I built
- Created an EventBridge rule to match GuardDuty finding events
- Used a Lambda function as the target
- Generated GuardDuty sample findings
- Verified Lambda invocations in CloudWatch Logs
- Confirmed real finding fields were logged, including:
  - severity
  - finding ID
  - finding type
  - account ID
  - region
  - title
  - description

### What this proved
A GuardDuty finding could automatically trigger:
- EventBridge event matching
- Lambda execution
- CloudWatch log output

This completed a real detection-to-response workflow inside the lab.

---

## Main Lessons

### Visibility
CloudTrail helped answer:
- what happened
- who did it
- when it happened
- whether the action was read-only or a write/change event

### Detection
GuardDuty findings were useful when interpreted with context instead of treated as automatic proof of compromise.

### Prevention
S3 Block Public Access prevented a risky public bucket policy from being applied.

### Hardening
Reducing root usage and separating admin from read-only access made the environment safer and more realistic.

### Response
EventBridge and Lambda turned GuardDuty findings into a real automated response path.

---

## Project Outcome
This lab started as a basic AWS security setup and grew into a complete progression:

- Foundation
- Investigation
- Hardening
- Response

The result was not just a configured AWS account, but a small cloud security environment where I could:
- observe activity
- investigate events
- reduce risk
- and automate part of the response flow

---

## Next Steps
- Build a second lab focused on investigation and response
- Correlate CloudTrail activity with GuardDuty findings
- Replace broad admin access with tighter least-privilege permissions
