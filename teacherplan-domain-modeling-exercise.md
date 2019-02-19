# TeacherPlan Domain Modeling Exercise

Imagine that a principal of a high school has approached you with a problem. She has a system to help the teachers at her school devise improvement plans for themselves, but it struggling to keep track of all of the paperwork involved with it. She wants to hire you to build an app tp help.

We want to make it easy for teachers and coaches to draft, discuss, revise, and approve improvement plans. See [this document](https://docs.google.com/document/d/1CVDEl5MJpaSIMH6ReWQq5AUft4RDE_CfHOASCDNWw8A/edit?usp=sharing) for real sample data.

Our goal is to come up with a domain model to capture this data, and support the following:

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

    **All of these except target date should just be free-form text fields**, like in the linked sample Google Doc above.
 - Any user can coach any other user. A user becomes a coach if they are invited to be one (by email address) by the owner of the Improvement Plan.
 - A user can have their own Improvement Plans, Improvement Plans they are coaching on, both, or neither. There should be a dashboard where the user can see all of the Improvement Plans they are connected to.
 - Owners and coaches for an Improvement Plan should be able to add comments on the Improvement Plan itself, and Goals within it.
 - Improvement Plans have five statuses:
    - Not yet submitted
    - Waiting for approval
    - Changes requested
    - Active
    - Complete

Try to come up with a domain model! Ask us any clarifying questions you have about the features of the app.

You can sketch your Entity Relationship Diagram (ERD) out on paper, or diagram it in [ideas.firstdraft.com](https://ideas.firstdraft.com/).