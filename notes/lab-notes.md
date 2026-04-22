# AWS Cloud Security Lab Notes

## Lab purpose
This lab is for learning AWS security in a practical way, with most of the focus on visibility, detection, and understanding what activity is happening in the account.

I understand the basic purpose of root, MFA, and IAM from Sec+ prep.
---

## Main focus areas
- CloudTrail
- GuardDuty
- S3 Block Public Access
- basic IAM least privilege as support

---

## What I want to get good at
- seeing what happened in an AWS account
- knowing where evidence comes from
- understanding what CloudTrail records
- understanding what GuardDuty is detecting
- recognizing why public exposure is dangerous
- explaining what a finding means and what I would do next

---

## Lab mindset
1. What does this do?
2. What does it log, detect, block, or allow?
3. Why does it matter from a security perspective?
4. What would an attacker abuse here?
5. How would I prove this is configured correctly?

---

## Phase 0 - Quick identity checkpoint

### Goal
Make sure the account is not built on a weak foundation

---

## Phase 1 - CloudTrail

### What I need to learn
- what CloudTrail is
- what event history is
- the difference between management events and data events
- what a trail does
- why logs need integrity protection
- why multi-Region logging matters

### Questions I should be able to answer
- What is the difference between CloudTrail event history and a trail?
- What is a management event?
- What is a data event?
- Why are data events not always enabled by default?
- Why is log file validation important?
- Why would a single-Region trail be weaker than a multi-Region trail?

---

## Phase 2 - GuardDuty

### What I need to learn
- what GuardDuty watches
- what a finding is
- severity levels
- how to read a finding
- what evidence supports the finding
- what response would make sense

### Questions I should be able to answer
- What does GuardDuty use to generate findings?
- Is every finding an active compromise?
- What makes a finding high severity?
- What should I verify before panicking?

---

## Phase 3 - S3 Block Public Access

### What I need to learn
- how public exposure happens
- what Block Public Access prevents
- why storage mistakes are security incidents waiting to happen

---

## Personal rule for this lab
I am not just enabling services.
I am learning what they mean, what risk they reduce, and how to explain them clearly.




