# GuardDuty

## Observations
- GuardDuty findings are not raw logs. They are interpreted detections.
- Severity is useful, but it is not enough by itself.
- Sample findings helped show how GuardDuty groups signals into a larger story.
- GuardDuty became more useful when tied back to CloudTrail evidence.

## What I noticed
- Low findings can still teach important lessons, like root credential usage.
- Critical and medium findings contain more context, including actors, resources, signals, and techniques.
- Similar IPs, tags, and resource names appeared in sample findings because the data was synthetic.
- GuardDuty count values did not mean total findings in the console. They showed repeated occurrences tied to the same finding pattern.

## What these tell me
- GuardDuty highlights activity that may be risky or suspicious.
- A finding should be read through context, not just severity.
- GuardDuty is more useful when paired with CloudTrail.
- Findings can also be routed into response workflows instead of only being viewed in the console.

## Later phase connection
GuardDuty was used in both investigation and response:
- investigation by tying findings back to CloudTrail context
- response by sending GuardDuty finding events to EventBridge and Lambda
