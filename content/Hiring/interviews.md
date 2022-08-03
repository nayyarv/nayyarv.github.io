Title: Some Technical Interview Questions 
Subtitle: Interviews, ML, decisions
Date: 2019-08-26 10:20
Category: interview
Tags: ds, advice, interviews
Authors: Varun Nayyar

I recently had the chance/misfortune to attend a lot of ML interviews and it's kind of given me a little insight into the industry as it stands right now. I wanted to share the way I interview and why I choose those questions. These questions are mostly ideal for a small/mid size DS/ML tech firm - smaller companies can't afford as much specialisation and niche areas of research will have people coming in quite unfamiliar that you don't want to reject unecessarily (a la Google) due to a much weaker recruitment pool.

This article really only applies to final interviews of candidates, but some ideas might bleed over to screening rounds too.

## The Rationale

At a smaller firm, the job title in ML is best described as Research Engineer. You need to have feet in both research and software since you need to be able to implement your ideas as well as roll out to production. You tend to get two different types here - maths majors who've learned to program well and programmers who've picked up maths. The first group tend to be PhD's (or dropouts) while the second group tend to be self taught in ML. 


## Considerations

1. It has to be about the fundamentals/basics 
    - You can't ask anything specific to your domain - it's likely to be niche, your candidate is unlikely to have skill in your particular area, and even if he's coming from a competitor, the way things done are so different, it's tricky to assume any level of skill. Fundamentally, you can't select for specific knowledge since either the interviewer is not proficient enough or the candidate isn't. 
    - Seeing if they stay up to date is really difficult since they may, but in an area you're not familiar in. And if they haven't read the latest paper in your space, that's not on them either.
    - You're trying to work out if they can learn new things. You're testing for intelligence, not specific knowledge.
2. Not everyone has experience with every algorithm. You can't ask someone about the details of a neural net if they've never trained one. Not having experience with torch/tensorflow is meaningless, most people never need to train neural nets and shouldn't, so it shouldn't be held against them. I call this the KL divergence criterion - measuring someone's skill should be independent of the interviewer's interests and skills.
3. It should give them a chance to go into depth. In order to be about the basics without being a quiz, it should allow the person to dive as deep as they are able. This gives them a chance to show off what they know. Because of this, I don't necessarily like the idea of 5 independent 45 minute interviews. I think it's a good idea to have the technical interview run a bit longer and reduce the number of interviews. 
4. You should decide on a rubric before you go into the interviewer. This can be modified as you get more experience, but reasoning about how marks should be allocated reduces your bias and also helps getting feedback from colleagues. It also forces you to think about how questions


## Cardinal Sins

1. Quizzes. Your interview questions should be good even when doing it open book. Questions like this are of limited benefit and tend to be good for someone fresh out of a data science bootcamp.
    - Vanishing gradients in Neural Nets
    - What are support vectors in SVMs
    - The difference between Boosting and Bagging
    Furthermore, these questions impinge on my principle of expecting full coverage of questions and not being good open book questions. They serve well as a screeners, but should be abandoned early.
2. Pure software interviews
    - Data Structures and algorithms are not good ways to interview ML engineers. There is some benefit, but a very large part of ML engineering doesn't go that low level since much of it is done in higher level languages that have plenty of abstractions. Most software engineers never really go into much depth in terms of Data Structures, most ML engineers even less. You'll reject many for no reason
    - These questions are easily gameable. Seeing the study guides for google et al, it doesn't seem like something you can compete with. Leetcode has nearly every interview and this has resulted in degeneracy in the interview process.
    - These questions have high false positive rates - many rely on tricks or familiarity. It's worth a simple one  as a fizzbuzz test but nothing more.
    - Software interviews are best combined with real world programming. I had an interview which asked me to implement malloc and free - this was a terrible interview for my skillset, but something that would be good to ask a software engineer. Another example was a key value DB that also kept the time values so you could get historical records too.
3. Brain teasers
    - This is very rarely a good idea - it can be a proxy feature of what you're looking for, but it's a very noisy way of getting that out. This was tried in discarded in the 2000s by most software firms.
    - Again, these are likely to select people who've seen the questions and also those who are lucky. It's also heavily dependent on the interviewers giving good hints. 


## General Principles

1. Tailor the interview to the candidate - ask them which areas of ML they're good at, or provide a few questions and give them a choice. For ML, you don't want to check their weaknesses, you want to test their strengths.
    - I've considered asking an interviewee what they'd prefer to be tested on and ask them to prep it and test them on that instead of giving a very broad interview.
    - If they have a publically available project, I think it would be a good idea to ask them to review it and write up a presentation on it. This could be a good way to determine their understanding of their core topic and comfort with presenting.
2. Take Home Interview Aside
    - this should be used judiciously. If a person has no experience and no portfolio, it's fair to ask. Less so for experienced candidates since they'll have other offers and not want to waste time on your interview.
    - Provide choice so the person gets to play to their strengths
    - Ensure the person speaks with someone on the ML team before asking for the assignment. If the person is clearly competent, it may not be necessary and might chase away competent people. It also gives them an indication of fit so they can choose to spend the time on the process
    - Offer payment at market rate (i.e. if you're paying 100k pay 50/hr). This prevents you from setting stupidly long assignments, shows committment to the candidate and provides a hard time limit. You should get this time limit from asking other members of the team to do this question and estimate time spent on it.
    - Provide a marking rubric - allow the candidate to understand what you value. It also ensures consistency across reviewers and if universities do so, so should you.
3. Workshop your interview - testing on a person currently working for the company is a good idea. You get an idea of how long the interview will take (add a multiplier for interview nerves) and if it's an interview that would pass your current colleagues. You should discuss interview questions with colleagues extensively and try it out on a couple of candidates with low confidence to check it's performaance in real world scenarios before moving it into the standard rotation.
4. These interviews require more work, but in a competitive market, a good interviewing experience can really help you stand out. They also give you a chance to get someone's best performance instead of the relatively noisy current interview style.


## My Questions (in progress)

### The Elevator Problem

Problem solving in a vacuum. No ML needed, but may bias towards Comp Sci majors since it is algorithmic. I like it since it requires one to state a few assumptions, come to a few simple insights and decide on it.

#### Question Statement

A residential building has 20 floors and 3 elevators. The current elevator algorithm chooses the nearest elevator and sends it to the requesting floor. You can assume that elevators are almost always used one at a time (i.e. there is never more than 1 requester and while he/she is in motion, no one else requests an elevator). 

1. Describe some scenarios which cause subpar performance with this algorithm.
    - Hint: consider what happens in the morning and the evenings during the week
2. Can you suggest some improvements to the algorithm to minimise waiting time for the residents
    - Note: the optimal solution is in research, so make sure they only try to come up with a good algorithm
    - Describe how your considerations would change for an office building
    - How would you evaluate your new algorithm?

#### Notes

- Tests Problem Solving ability and taking poorly defined questions and reasoning about them
- Stress to candidates that this is not an ML question, just something more deterministic
- Many problems require simple solutions - recognising that is a good sign
- Meta level considerations (feasability of having ML in elevators) is usually a good sign. 
- Extra bonus - simulate some data and then evaluate the improvements. Also tests coding ability

### Design a Neural Net

Good mix of software systems design and ML considerations. I really like this since neural nets are so simple but have a few design decisions. Additionally, almost every ML person will have some understanding of how Neural Nets work and this requires very little prior knowledge. This should be done open book. 

There are many ML points to consider that allow for an in depth look into their ability to reason. It's also not some annoying string search algorithm that is very gameable. 

#### Question Statement

We live in a world where torch and tensorflow don't exist. You want to build your own neural net using just numpy. It should
    
- Support an arbitrary number of layers
- Have Fully Connected Layers and TanH activations out of the box
- Do SGD for optimisation
- (Bonus 1) custom learning rate
- (Bonus 2) Momentum SGD - this can be tough

You can assume

- No GPU acceleration
- Infinite RAM 
- No RNNs
- data is a single (shortish) vector


#### Notes

- Longish interview, systems design esque. 
- This can double as a behavioural interview and see how they respond to criticism and suggestions
- Arbitrary changes should be proposed to see how they handle design. 
    - Dual Fully Connected Layers (W1 @ x2 + W2 @ x2) should be an interesting mixup
    - Skip Layers?
    - How would they implement Transfer learning
- This can be adapted to implementing a particular simple algorithm that they're familiar with. Doing Bayesian Linear regression via MCMC achieves a very similar outcome for someone who's familiar with Bayesian methodology


Many points of discussion, a few below:

    - How to initialise - why ones and zeros is bad for weight matrices.
        - I.e. backprop is slow and imbalanced 
    - Shape of state of the FC layer. Column major vs row major? 
    - How to save the x for the backward pass? Design choice
    - How to implement the optimiser
    - Do they write tests - can they check it works
        - A set of tests is very good to see if they're considering how it's going to be used
        - Checking that training a net on random data reduces loss is good (suggest providing loss function and derivatives for speed)
    - Discussion on numerical considerations (i.e. logs and small numbers, requiring the combination )


## Further Questions

To be added

Implementing ML algorithms is a great exercise - it doesn't have to be a neural net, but they can choose an algorithm they're most familiar with. 

    - A simple tree algorithm is another great one. 
    - MCMC is another algorithm that is super easy to implement and can be tested on anscombe's quartet
    - Linear Regression is a bit too simple, so make sure they add more diagnositcs and I would suggest using tro


## ML & DS today

Opinion

1. ML/Research Scientist - Almost exclusive to large organisations, these are commonly Postdocs with strong publication records who've left academia because of the insane competition for tenure and ply their trade on complex problems. Since large companies tend to have a lot of infrastructure and support, these people tend to come in very specialised since the scale and depth of these problems is very different. For example, the Google Assistant is world class (especially with varying accents) and this level of performance is very research intensive.
2. ML Engineer (Large Company) - The scale at large companies results in a split of the ML roles into scientist (Above) and engineer. Most of this is focussed on things like data pipelines, clusters, implementing algorithms from scientists, scaling up to a cluster or even working with scientists to adapt algorithm for scale. This is much closer to a pure SWE than an ML engineer at a smaller company.
3. ML (Small/Mid company) - specialisation is not really something the company needs and requires. R&D, ops and deployment are tightly knit and there is a significant need to share duties. Problems are less cutting edge and the scale is much smaller. Full datasets will likely fit into RAM so large scale sharding and infra is significantly less important here. The role of engineer and scientist tends to blend together here with the job best being described as a research engineer. There is expectation to develop the algorithms and deploy them as well as maintain all the infrastructure necessary. This is a tricky position to hire for, since it's very rare to find high level skill in research and software. This merged skillsets are conversely less valuable in a large company, so make sure to not copy and paste requirements - being open is your best bet for finding a good fit.
3. Data Scientist - this role is the worst defined. This role is most commonly found in non-tech firms, but not always. There tends to be a combination of the top 3, but most of the algorithms and software tends to be off the shelf. This job in many ways tends to be a mixture of software engineer and domain expert, or a progression of the Data Analyst. Going beyond off the shelf requires tends to require a full ML team, and the Data Scientists here tend to be using internally built tools and techniques and reporting to the central team developing algorithms for problems. This role is still in flux and will likely be for a while. Any company of significant size will start moving towards ML engineers with math expertise and Data Scientists with domain expertise.
