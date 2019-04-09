# TeacherPlan Domain Modeling Exercise

Imagine that a principal of a high school has approached you with a problem. She has a system to help the teachers at her school devise improvement plans for themselves, but it struggling to keep track of all of the paperwork involved with it. She wants to hire you to build an app to help.

Examine [this document](https://docs.google.com/document/d/1CVDEl5MJpaSIMH6ReWQq5AUft4RDE_CfHOASCDNWw8A/edit?usp=sharing) to see what a real Improvement Plan looks like. This doc represents one Improvement Plan, for a teacher named Smith. The plan has three SMART Goals; each SMART Goal has 4-5 Action Steps.

After a teacher drafts an Improvement Plan, it has to be approved by a coach (which can be the principal or another teacher at the school). This usually involves some back and forth, where the coach asks the teacher to add or modify some SMART Goals or Action Steps.

Currently, documents like the one above are being filled out and various versions of it are being emailed back and forth between multiple parties, things are unsurprisingly slipping between the cracks, and due dates are being missed.

We want to make it easy for teachers and coaches to draft, discuss, revise, and approve Improvement Plans. Our goal is to come up with a domain model to capture the data in the linked doc, and support the following:

 - As a teacher, I want to sign up (first name, last name, school email address).
 - As a teacher, I want to create an Improvement Plan.
    - An Improvement Plans has a description.
 - As a teacher, I want to add one or more Goals to my Improvement Plan.
    - A Goal has a description. 
 - As a teacher, I want to add one or more Action Steps to my Goal.
    - An Action Step has
        - a description
        - a target date
        - people who take the lead on it (this can be anyone, not necessarily one of our users)
        - resources needed
        - implementation specifics
        - measures of success
 
    **All of these attributes of an Action Step, except target date, should just be free-form text fields**, like in the linked sample Google Doc above.
 - As a teacher, I want to invite one or more other teachers to act as coaches for my Improvement Plans (invitations are sent via email).
    - Any one of our users can coach any other user, as long as they've been invited.
 - As a teacher, I want to see all of the Improvement Plans that I am connected to; since I can have my own Improvement Plans, Improvement Plans I am coaching on, both, or neither.
 - As a both an owners and a coach for an Improvement Plan, I want to comment on an Improvement Plan itself, and on Goals within it.
 - Improvement Plans have five statuses:
    - `Not yet submitted`
    - `Waiting for approval`
    - `Changes requested`
    - `Active`
    - `Complete`
    
    As the owner of an Improvement Plan, I want to update its status from:
    
        - `Not yet submitted` to `Waiting for approval`
        - `Changes requested` to `Waiting for approval`
    
    As a coach for an Improvement Plan, I want to update its status from:
    
        - `Waiting for approval` to `Changes requested`
        - `Waiting for approval` to `Active`
        - `Active` to `Complete`
        
    As the owner and as a coach, I want to receive an email when the status of an Improvement Plan changes.

Try to come up with a domain model! Ask us any clarifying questions you have about the features of the app — you will invariably come up with some questions the moment you start trying to design your tables.

I recommend starting by drawing out your tables fully, like the printed out databases from last week for Must See Movies and Photogram, and trying to enter in some rows to make all information has a place to live.

Then, you can transfer your database design to the more compact Entity Relationship Diagram (ERD); either on paper, or diagram it in [ideas.firstdraft.com](https://ideas.firstdraft.com/).

## My proof-of-concept workflow

My usual flow for spiking on a proof-of-concept is:

 - Identify the pain point.
 - Sketch out some super low-fidelity screens in the application — what will a user see when they first sign in? Where can they navigate from there? "Crawl" the app to identify the most important screens.
 - See what _information_ and _actions_ are present on the screens. These map to Create, Read, Update, and/or Delete, somehow (or calculations on data that we've already got).
 - Write down a list of the most important user _capabilities_ — I like to hew roughly to the [User Story](https://www.romanpichler.com/blog/10-tips-writing-good-user-stories/) format, for simplicity and standardization:

    "As a [role], I want to [capability]," (and, optionally), "so that [benefit]."
 
     I've already sort of written these down above.
 - Get my hands on some real data that's being used to do these jobs already; usually, somehow, somewhere, they are already happening, perhaps inefficiently.
 - Finally, with user stories and real data in hand, try to design my database tables; either drawing them out fully (with columns and rows), or skipping directly to the ERD format, or jumping back and forth.
 - With a complete ERD — i.e. all tables and columns, including foreign key — in hand, I'm great shape to start writing code.
