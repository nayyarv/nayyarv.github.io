Title: A/B testing / Bandit Methods
Subtitle: Resources and Skepticism
Date: 2018-10-22 10:20
Category: advice
Tags: critique, ds, advice, ab, bandit
Authors: Varun Nayyar

This is a short article, primarily full of resources. I assume some basic knowledge of A/B testing

## A/B testing

I must start posting Evan Miller's articles on the subject which I consider a fantastic resource in this area. 

1. [How not to run an A/B test](https://www.evanmiller.org/how-not-to-run-an-ab-test.html) - never end an A/B test before it's allocated run time.
2. [Sequential A/B testing](https://www.evanmiller.org/sequential-ab-testing.html) - How to run an A/B test that allows for stopping early without ruining results. 
3. [Bayesian A/B testing](https://www.evanmiller.org/bayesian-ab-testing.html) - a Bayesian approach that allows one to 'peek' whenever necessary.

Additionally, this article on [statstical power](https://www.evanmiller.org/the-low-base-rate-problem.html) is also something worth reading as it touches on assessing significance as your click and lift is low - basically the lower the success rate is, the more samples you need to ensure that you've reached significance.

### A/B Testing Summary + Critique

1. All the approaches of A/B testing use the same tech backend. The Sequential and Bayesian approaches allow for checking the results partway through, so there is an expectation that you can check on your results every so often, and maybe even automate this part
2. Traditional A/B testing is the most robust approach - if you use an early stop version, you run the risk of catching significance on a certain day. For example, testing a greeting that uses "Monday" performs better on monday and might show significance that wouldn't be ther when run over a period of a week.
3. Generally speaking, the bayesian approach is preferred over sequential testing. Or at least has found more wide adoption. This is primarily because you still need to choose a sample size at the beginning, a restriction not present in the bayesian approach.
4. There is a lot of debate over traditional a/b testing vs bayesian methodology, and the basic answer is that it's not that important. If you want robustness, go traditional, if you expect a big lift, go bayesian so you can stop the experiment as soon as you're confident in the results.
5. The traditional A/B testing is much better known, is easier to implement and is less likely to confuse someone than a bayesian approach. Frequentist results are easier to misinterpret than Bayesian results, but bayesian results are harder to arrive at.
6. Bayesian methods are more computationally intensive than the equivalent frequentist statistics and has fewer well known implementations. 

[This article](https://conversionxl.com/blog/bayesian-frequentist-ab-testing/) runs through the various differences in much greater detail.
[And this article](https://conversionxl.com/blog/12-ab-split-testing-mistakes-i-see-businesses-make-all-the-time/) lists a few other common errors common in A/B testing in real life, with a very heavy web bias. 
A/B testing does exist in other scenarios (traditionally in use of new medical treatments), but the Web has been a much more fertile ground for turning this up to 11. The original ethical concerns of stopping an effective medical trial early have only been approached in the internet age.

## Bandit Methods

[Bandit methods](https://lilianweng.github.io/lil-log/2018/01/23/the-multi-armed-bandit-problem-and-its-solutions.html) are the other side of the coin which basically approach the problem of trying a few different methods, seeing the success of one over the other and presenting the more successful one more often. 

More precisely, we set a parameter epsilon which is an indication of our exploration rate that we reduce over the period of our testing (a week for example). We then choose a random page if epsilon > random() otherwise, we serve our best page. 

Bandit methods are a similar response to traditional A/B testing, the question of regret. When you have a better method (say a donation webpage) that's outperforming your old one, you lose a lot of money for each day you run the A/B test. Also, if you run a lot of A/B tests, setting up and analysing at the end is always a pain, can you set you

### Bandt Summary + Critique

1. A more involved tech stack. While A/B testing simply records result of web A/B interaction, bandit methods need to store result of the interaction and then work out which webpage to show based on past results. Unlike a simple random call to determine which page to show, the code at the delivery layer is a bit more involved. This is likely the big issue
2. Bandit methods are quite fragile - they rely on instant feedback to adjust the probability of returning the best value. Email campaigns or conversions that are non-instant break the fundamental assumptions of bandit methods and can lead to it acting quite erratic.
3. Similarly to above, a certain day of the week can push a bandit method into prime position that stays at the top for a while. Contrastingly, a bandit method won't realise that a certain page is more effective on certain days. 
4. Bandit methods need careful consideration of setup and exploration. Since the exploitation tends to favour one over the other, using it tends to result in a massive imbalance, and you can converge to non-ideal answers.
5. Knowledge of the distributions involved allows you to put a bayesian spin on the answer. In particular tracking the upper confidence bound is generally a better idea since you get more certainty the more you exploit and you include potential value in your equations
6. Bandit methods don't give you inference - the imbalance means you don't ever have a sample size that's big enough in both categories to give you the inference you're after. At the end of a bandit run, you're unlikely to be completely sure you've found the best answer, though you can try various strategies to ensure the certainty

## Bandit vs A/B

[This post](https://conversionxl.com/blog/bandit-tests/) is a fantastic resource on this and does a much better job than I could on the question.

1. The basic conclusion is that Bandit's when done well are powerful approaches, but also require an organisation to be completely behind the system. 
2. Considerations from A/B tests (running for a week at minimum, public holidays) need to be applied to Bandit methods too.
3. Drawbacks of bandit methods, mainly need for instant feedback, should disqualify these methods when instant feedback is not possible.
3. Bandit methods are great way to run continuous a/b tests without the need to involve a Data Scientist. Designers can upload new pages and can see if the pages are working better.
4. Bandit methods are less complex to scale than an A/B/n test.

Finally it doesn't really matter. Bandit methods are a natural evolution for an org that has realised the value of A/B tests and is constantly running tests. It's unlikely you'd go from no testing to bandit methods, and A/B tests are a very robust way to approach this problem, perfect for a beginner in this space.