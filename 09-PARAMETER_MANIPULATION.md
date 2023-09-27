## Location :
In the survey section

## Type of Vulnerability :
Parameter manipulation

## Explanation
We inspect the code and notice that we can easily change the value of the boxes when we vote, let's try with a huge value ``1000000000``
-> We get the flag

## Risks
- Data alteration
- Unauthorized access to functions or data
- Opening to certain types of DoS (Denial of Service) attacks

## How to Fix
- Backend validation
- Use of form token
- Implementation of action quota (limit over time on the number of times an action can be performed by a user)
- Input checking and data integrity validation
