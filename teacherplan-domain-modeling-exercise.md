# TeacherPlan Domain Modeling Exercise

We want to make it easy for teachers and coaches to draft, discuss, revise, and approve improvement plans. See [this document](https://docs.google.com/document/d/1CVDEl5MJpaSIMH6ReWQq5AUft4RDE_CfHOASCDNWw8A/edit?usp=sharing) for real sample data.

 - A user can create an Improvement Plan.
 - Improvement Plans have one or more Goals.
 - Goals have one or more Action Steps.
 - Action Steps have
    - description
    - target date
    - people who take the lead on them (this can be anyone, not necessarily the user)
    - resources needed
    - implementation specifics
    - measures of success

    All of these except target date should just be free-form text fields.
 - Users should be able to add other users to their Improvement plans to act as coaches.
 - Any user can have their own improvement plans (but don't have to), and be coaches for other users. Users should be able to see both their own plans and plans that they are coaching on.
 - The coaches and the owner of improvement plans should be able to add comments on the plan itself and on each goal within it.
 - Improvement Plans should be in one of five states:
    - Not yet submitted
    - Waiting for approval
    - Changes requested
    - Active
    - Complete

Try to come up with a domain model!
