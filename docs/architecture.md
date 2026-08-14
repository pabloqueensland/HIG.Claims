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
- The system needs to be reliable: Every claim needs to be processed and reach an end state. Transient failures should be retried automatically up to a defined retry limit. Upon surpassing a set amount of retry attempts it will be marked as failed, where it can be reviewed. Retries can be reset manually.
- Expected through-put: 200 requests/h average.
- API Response time: Response times should be instant (under 1 second)
- End-to-end Response time:  a claim needs to reach and end state in 1 to 2 minutes, depending on external apis.
- Claim visibility: At any given time users need to be able to query necessary data in an useful format.
- Observability: The system muse expose enough logs, metrics and tracing information to diagnose processing failures, retry behavior, latency and external dependencies.
- The system needs to be able to maintain acceptable response times and reliable claim processing as the volume of requests increases. 

## High-Level Design
<img width="565" height="780" alt="image" src="https://github.com/user-attachments/assets/9f9d2bc5-f0b3-4f2e-b984-ba6b093c7222" />


## Claims Processor Consumer Worker
<img width="598" height="758" alt="image" src="https://github.com/user-attachments/assets/26848e0d-a282-4cbf-bf73-0b755ebb6c4c" />

## Claim States
-1 - Failed
0 - Received
1 - Processing
2 - Aproved
3 - Rejected
4 - ManualReview

<img width="583" height="319" alt="image" src="https://github.com/user-attachments/assets/21c6dfc6-8eb4-4886-9916-224347a555aa" />

