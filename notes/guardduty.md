# GuardDuty

## Observations
- GuardDuty findings are not raw logs. They are interpreted detections.
- Severity is useful, but it is not enough by itself.
- Sample findings helped show how GuardDuty groups signals into a larger story.
- Attack-sequence findings showed how multiple suspicious actions can be correlated.

## What I noticed
- Low findings can still teach important lessons, like root credential usage.
- Critical attack findings contain much more context, including actors, resources, signals, and techniques.
- Similar IPs, tags, and resource names appeared in sample findings because the data was synthetic.
- GuardDuty is more useful when treated as a decision-support layer, not as perfect truth.

## What these tell me
- CloudTrail shows what happened.
- GuardDuty tells me what may be risky or suspicious about what happened.
- A finding should be read through resource context, identity, affected service, signals, and timing, not just severity.
