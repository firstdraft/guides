# A few readings on managing software products

## Workflows

### A very powerful Git flow

This is behind a paywall (but there's a trial period). It's very low-level and tactical, so it might be hard to understand right now; but you should refer developers that you work with to it, and they should either have a flow similar to this one, or *very* good reasons for using something different:

[thoughtbot's Git Flow](https://thoughtbot.com/upcase/videos/git-thoughtbot-git-flow)

###  Kanban/Trello Workflow

[An overview of a Kanban-like process for product management.](https://robots.thoughtbot.com/how-we-use-trello-for-product-development)

[More details about using Trello for product management.](https://gist.github.com/raghubetina/7b5303df29c63b1a0e68156eece54ac2)

### Code Review

One of the most common questions I hear is, "How do I keep my team happy / how do I retain good developers?"

One of the most important components of staying happy for developers is feeling like we're always continuing to learn.

One of the best ways to promote learning on a team is a strong Code Review Culture.

 - It feels great to get alternative ideas on how to attack a problem right when you are setting out. Often, someone else on the team can alert you to a different approach that you hadn't considered or heard about.
 - You would be surprised at how often a junior developer can teach a senior developer a new trick.
 - And, obviously, Code Review is an incredibly good way to train junior developers.
 - Code Reviews demolish knowledge silos, reducing your risk.
 - Oh, and they helps catch bugs sometimes, too.

[A low-level walkthrough of how to perform productive code reviews.](https://thoughtbot.com/upcase/videos/tips-for-code-review)

[A high-level perspective on how and why to implement a strong Code Review culture. ](https://www.youtube.com/watch?v=PJjmw9TRB7s)

### Playbook

[The development section of thoughtbot's Playbook (the whole thing is worth a read).](https://playbook.thoughtbot.com/#developing)

## Technology Choices

[*Choose Boring Technology*](http://mcfunley.com/choose-boring-technology):

> Let's say every company gets about three innovation tokens. You can spend these however you want, but the supply is fixed for a long while. You might get a few more after you achieve a certain level of stability and maturity, but the general tendency is to overestimate the contents of your wallet. Clearly this model is approximate, but I think it helps.

> If you choose to write your website in NodeJS, you just spent one of your innovation tokens. If you choose to use MongoDB, you just spent one of your innovation tokens. If you choose to use service discovery tech that's existed for a year or less, you just spent one of your innovation tokens. If you choose to write your own database, oh god, you're in trouble.

I believe Rails is this kind (the good kind) of "boring".

A counterpoint: [*Why I wouldn’t use Rails for a new company*](https://blog.jaredfriedman.com/2015/09/15/why-i-wouldnt-use-rails-for-a-new-company/). The author's basic thesis is to "skate where the puck is going" in terms of developer enthusiasm/mindshare, which makes sense.

However, I don't believe that there is a clear successor to Rails -- yet. The author mentions Node.js, but I believe that it has already stabilized in mindshare. [Elm](http://elm-lang.org/) and [Phoenix](http://www.phoenixframework.org/) are both showing promise, but they still aren't even close to having a rich ecosystem of "gems" and Stack Overflow answers like Rails has, so you will be spending some of your "innovation tokens" re-inventing things that the Rails community has already solved.

Here's DHH himself on the topic: [What makes Rails a framework worth learning in 2017?](https://www.quora.com/What-makes-Rails-a-framework-worth-learning-in-2017/answer/David-Heinemeier-Hansson)

## Estimations

[A guide to producing software estimates.](https://www.atlassian.com/agile/estimation)

A counterpoint: [*Why software estimation is a losing game*](https://rclayton.silvrback.com/software-estimation-is-a-losing-game)

I tend to agree with the latter.

## Hiring

[A collection of essays from Basecamp on Hiring.](https://m.signalvnoise.com/hiring-a-programmer-ditch-the-coding-interview-and-get-back-to-basics-f5c43e369eaf#.ow48v5rjz)