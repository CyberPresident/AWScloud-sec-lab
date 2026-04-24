# S3 Block Public Access

## Observations
- Account-level Block Public Access was enabled with all four settings turned on.
- The CloudTrail log bucket had a bucket policy but was still not public.
- A service specific bucket policy is different from a public bucket policy.
- A public read style policy attempt was rejected.

## What I tested
- Checked account level Block Public Access settings
- Reviewed the CloudTrail bucket permissions
- Created a throwaway S3 bucket
- Tried to apply a public read bucket policy
- AWS rejected the change because it conflicted with Block Public Access settings

## What these tell me
- Having a bucket policy does not automatically make a bucket public.
- AWS can allow a tightly scoped service policy while still blocking public exposure.
- Block Public Access is a prevention control, not just a visibility feature.
