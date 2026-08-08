## Current Scenario

At the moment we have a claims endpoint that receives an average of 1500 requests per day. 
Since these requests happen mostly in Australia, most requests happen between 8am and 4pm AEST, 
with peaks of 200 requests/h avg from 9 to 10am and 1 to 2pm, which would mean peak input of 4 req/min average, with a maximum burst of 20 claims in a minute.
