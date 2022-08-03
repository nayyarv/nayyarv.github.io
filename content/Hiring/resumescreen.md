Title: Bayesian Resume Screening
Subtitle: Screening Resumes and Pitfalls of Bias
Date: 2018-09-03 10:20
Category: advice
Tags: bayesian, ds, advice, interview, resume
Authors: Varun Nayyar
Status: draft

Like all enthusiastic idiots, I thought it would be a great idea to help in interviewing and resume screening. Unfortunately, this meant that I ended up reading a lot of resumes and started to develop my own model of what was important, from education to portfolios and things in between. I assume you're going to have an exhaustive interview process anyway, so resume screening really should be about finding people with potential, rather than scouring for potential.

We all have biases, I've done this work in many fields now so I think my bias is relatively even, though my background (math/engineering degree, started down PhD path, but walked away) is still fairly biased.

## Education/Background

I have strong belief that a degree with quantitative backing is vital. Degrees like Maths, Physics, Engineering, Computer Science and Econometrics are generally degrees that form the foundations for a good data scientist. Most degrees don't just teach foundations, but also mould the way a person thinks. My Maths degree makes me more analytical, rigorous and skeptical, while my engineering degree was focused on getting results no matter what hacks were needed. And it's important to have a wide range of skills and make-up in your team as you'll encounter various problems that require different kinds of thinking and approaches. Having a team with no educational diversity results in very narrow thinking and is something you should seek to avoid.


### The Good

1. Computer Science Majors - these are probably the more dominant group in Data Science today. Primarily because there is a large amount of programming skill required to be able to DS and a comp sci major already has that down pat. They also have strong-ish maths skills, as computer science deals with a lot of discrete maths so they have a strong foundation to build on. Very good employees to have at any stage of your company. They have a lot of value at the beginning of DS in a company as they have enough software experience to get you off the ground and as your process improves, the amount of code required increases exponentially. 
2. Stats/Maths/Physics (Science) Majors - less dominant, but equally important, they form the other side of the coin, in that they're much stronger in the foundations of maths, but tend to have less programming skill. They're usually very well versed in different approaches and bring a degree of rigour and skepticism that's required to build great models. Again useful at all stages, as they bring simple approaches to bear in the beginning, but also tap into more advanced techniques as required and usually tend to stay on top of what's happening in the field.
3. Engineering majors - Engineers are a halfway optimisation between comp sci and science in this field, though many of them don't have a full background to be useful straight away. However, they generally make fantastic project managers, as they tend to be results driven and very aware of pitfalls in planning and also fantastic at turning problems into data science questions. In many ways, this unlocks a lot of value from your team and are ideal people to have if you feel like your DS team gets stuck and flounders a lot. 
4. Economics majors - (I haven't had a lot of exposure) What these majors tend to provide is a lot of lateral thinking, strong attempts to understand the domain that they're trying to improve, and an understanding of how to present DS ideas to non-technical people well.

Again, these are more tendencies than specifics, there'll be comp sci majors with better mathematical foundations than most maths/stats majors and maths/stats majors with better programming skill than most comp sci majors.

I love cross majors, comp sci/stats tend to give the best of both worlds in terms of foundations.

### The Doubts

1. Comp Sci - are almost always obsessed with Neural Nets of all kinds. They also tend to lack a strong statistical base and many regressions and Bayesian approaches mean nothing to them. They come with strong biases and might need to unlearn a lot of them and this can be an issue. They rarely bring any rigour to the table and are almost always overly confident about the performance of a model of theirs. There is also diminishing returns in comp sci skill in DS, the open source community puts together efficient implementations, so past a certain point, programming skill is less necessary than software architecture skill.
2. Maths/Stats - many can barely program and require a lot of training to be useful in this field. If you're unlucky, they'll even consider programming beneath them. And they're severely constrained by their need for rigour and are very dour about their results, which means good models they build might go unnoticed. Require very careful management
3. Engineers - tend to be middle of the road in both mathy and comp sci skills and don't really push your team forward in many ways. Over reliance on short term results can mean sacrificing longer term goals which they don't see as well. May also not get any respect from the comp sci/math majors
4. Economics majors - they also come with awful mathematics and programming skills, and are unlikely to have the insight as they were probably stars in their own fields.

## Higher Education (PhDs)

Overall, I'm mixed. PhD > undergrad, but PhD = Undergrad + 3 years experience. I think PhDs tend to be overrated, but are a safer bet than untested undergrad. I think experience + degree/PhD is the best combination.

### The Good

PhDs mean that the person who did them is very self-directed, self motivated and has the ability to learn by themselves, all of which are great features to have in an employee. Assuming a quantitative PhD, they likely have very strong skills in this area that are likely to be of instant use to you. Additionally, given that PhDs are usually from the top undergrads, you have a guarantee that they're generally more intelligent. PhDs tend to be people you need if you're on the cutting edge and are very good for raising the ceiling of your teams ability.

### The Doubts

The main problem is that a PhD doesn't really tell me that much about a person's ability to be an employee. Research and corporate environments are very different and success in one doesn't always translate. The PhD tends to be a very specific and sharp area, [see this comic](http://matt.might.net/articles/phd-school-in-pictures/) and while they've got more general skill, they're not necessarily much better than an undergrad, especially if you expect to have a bunch of different problems to solve. Additionally, the PhDs tend to be very top heavy the ones that are intelligent and have the ability to transfer skills, are likely ones to stick around in academia too. Basically a PhD applying is likely more intelligent than an undergrad, but you also know that they probably weren't the best of their cohort.

## Portfolio/Github

I used to love these things, but I now realise that it's quite a biased way to hire. The presence does make me go from a maybe to a yes, but the lack of one doesn't make me go no.

### The Good

It's always fantastic to see a Github profile and portfolio - you instantly get an idea of the candidate's programming ability and a portfolio gives you an insight into how they think and what models they're familiar with. PR to public repos are strongly indicative of an ability to work in a corporate DS environment, and proof they've solved a real world problem with a DS technique is more evidence. 

Additionally, this shows curiosity, which I consider a huge thing in a person. A curious person can be depended on to keep learning, improving and getting better. I argue a curious person with limited skill has more potential than a skilled by uninterested person. 

### The Doubt

Github and Portfolio's are very biased towards comp sci type majors, either studying or working in a small firm/startup. 

As stated before, there is a diminishing return for programming skill, but there is also a high bar to entry. This means people who have the ability to download, parse and write some code to run a simple model are more likely to have portfolio's than someone with the ability to conceptualise more complicated models, but need help to see that through. Now requirements might differ, but programming is an easier skill to lean than thinking mathematically. 

Despite pytorch being written by facebook, tensorflow by google, nearly all the blogs I read on how to use it have been written by people working for a .io or someone at university. As I read somewhere (and have experienced myself), working in a leading tech firm is like working in an alternate reality - they've made developments they've kept secret, but as the open source community has put out their own approaches, the rest of industry has fallen in line of the path of the open source implementations. Which means google and facebook employees have hard skills almost entirely based on non-open tech stacks and while they have ideas on how to solve the problem, they are unfamiliar with the prevailing packages and thus don't really have much to write about. Even startups that came up in the time between tensorflow and pytorch probably wouldn't write blogs about pytorch, again for the same reasoning.

## Experience

This is only a good thing, so I'm not going to split sections up, but instead point out things I like to see

- Versatility: If their experience shows a wide variety of problems being solved, that's good, because it shows they're not overly biased to one methodology and they have a wide exposure to methods to solve problems and a very strong sense of good process as approached by many places.
- Soft Skills: Hard skills are very rarely transferable. A lot of hard skill in a company is getting used to the way things are done and replicating that skill. Look at things like process changes, picking up things quickly, testing methodology and 
- Curiosity: Hard to generally tell from a resume, but curiosity is a thing that makes for excellent employees. You can tell a lack of it relatively easy if the resume looks cookie cutter.
- Company profile: elite companies in the resume are always strong indicators of success. There are many niche industries out there that are also elite so do make sure to do your research. I also tend to prefer experience in small-mid companies as this usually results in a much better overall skillset, while people in large companies tend to be overspecialised, though this can cut both ways.

## My Red Flags

- Poorly Presented Resume: This job has a huge amount of communication and if the applicant can't put together a resume that looks reasonable and clean, this might be a problem.
- Matlab: This is a personal peeve of mine, but Matlab on your resume indicates a lack of curiosity in the applicant. I used matlab (it's still one of my top linkedin skills for some reason) and didn't like it, so I sought better alternatives. If you haven't done that, chances are you're not going to have insight into your work.

## Conclusion

Overall, none of the areas can be taken in isolation. A non quant degree but 10 years in google DS mean something, while a PhD in Comp Sci and 5 years building apps builds another story. It also depends on your company, whether you have a large profile and get good applicants, or you need to interview to find diamonds in the rough.

More than anything else, be aware about your stereotypes and biases in hiring when looking at a resume. We tend to want to hire people like us/fit the company profile and so tech heavy companies hire coders who can do maths, while many consultancies hire problem solvers who can code and do maths, quant firms hire maths guys and try and teach them to code. This sometimes work, but diversity of thought is always important, I 