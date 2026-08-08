## Current Scenario

At the moment we have a claims endpoint that receives an average of 1500 requests per day. 
Since these requests happen mostly in Australia, most requests happen between 8am and 4pm AEST, 
with peaks of 200 requests/h avg from 9 to 10am and 1 to 2pm, which would mean peak input of 4 req/min average, with a maximum burst of 20 claims in a minute.

## Business Requirements
- The system must accept insure claims through an HTTP endpoint.
- Claim submission must return quickly without waiting for full processing.
- Every accepted claim must eventually be processed, regardless of the result of the claim.
- Claims must progress through validation, fraud checking, risk assessment and decisioning.
- A claim may result in Approved, Rejected or Manual Review.
- Support staff must be able to view the current status of a claim.
- Duplicate processing shouldn't cause duplicated business actions.
- Failed claims must be recoverable or manually retriable.

## Non-Functional Requirements
