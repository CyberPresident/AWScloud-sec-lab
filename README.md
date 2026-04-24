# AWS Cloud Security Lab

## Overview
This lab focused on building a secure AWS foundation and learning how cloud security works across different layers:

- **Visibility** with CloudTrail
- **Detection** with GuardDuty
- **Prevention** with S3 Block Public Access

The goal was not to build a huge environment. The goal was to understand how AWS records activity, how suspicious behavior is surfaced, and how basic storage misconfigurations can be prevented before they become exploits.

## Services Used
- AWS IAM / IAM Identity Center
- AWS CloudTrail
- Amazon GuardDuty
- Amazon S3
- AWS Budgets
- CloudWatch billing alerts

## What I Completed

### 1. Secured the AWS account for lab use
- Enabled MFA on the root account
- Avoided root use for normal day-to-day work
- Created administrative access through IAM Identity Center
- Added billing guardrails

### 2. Built the first visibility layer with CloudTrail
- Reviewed **Event history** before creating a trail
- Observed sign-in activity, IAM-related setup actions, and account changes
- Created a trail for ongoing log delivery
- Verified CloudTrail setup activity through real event records
- Reviewed raw JSON event scripts to understand how AWS represented actions and policies

### 3. Studied detection with GuardDuty
- Enabled GuardDuty in the lab account
- Generated and reviewed sample findings
- Compared low-severity policy findings with higher-severity attack findings
- Learned that severity alone is not enough and that findings need context, affected resources, and signal correlation to be read correctly

### 4. Tested prevention with S3 Block Public Access
- Verified account-level Block Public Access settings were enabled
- Compared a service-specific CloudTrail bucket policy with a truly public-style bucket policy
- Created a throwaway test bucket
- Attempted to apply a public-read bucket policy
- Confirmed AWS rejected the change because it conflicted with Block Public Access settings

## Key Lessons

### CloudTrail
CloudTrail showed me the difference between **event history** and a **trail**. Event history gave short-term visibility into recent management activity, while the trail created ongoing log delivery to S3 for longer-term evidence collection.

### GuardDuty
GuardDuty taught me how AWS moves from raw activity to interpreted findings. The main lesson was that a simple finding is not automatically proof of compromise. Severity matters, but resource context, signal correlation, identity details, and event patterns matter more.

### S3 Block Public Access
This phase made the clearest prevention point in the lab: a bucket policy existing does not mean a bucket is public. AWS allowed the CloudTrail service-specific bucket policy because it was non-public, but blocked my attempt to save a public-read style policy.

## Why This Lab Matters
This lab helped me understand three different layers of cloud security:

- **Evidence**: CloudTrail records what happened
- **Detection**: GuardDuty highlights behavior that may require investigation
- **Prevention**: S3 Block Public Access can stop an unsafe storage configuration before it becomes an exposure

## Next Steps
- Build a second lab focused on investigation and response
- Correlate CloudTrail activity with GuardDuty findings
- Replace broad admin access with tighter least-privilege permissions
