Title: Resume

## WORK EXPERIENCE

### Staff Research Engineer, Jan 2020 - Present

*Autumn Compass, Sydney*

- Increased sim-PNL by 20% by moving our black box optimiser to CMA-ES and taking advantage of training similar instruments together to reduce overfit.
- Developed profitable trading on ASX that did daily turnover of ~7 million AUD, resulting in broker fees being cut by 30%.
- Reduced incidents by 95% and increased researcher productivity and system quality by hiring an SRE to dedicate development time to infrastructure and operations,
- Sped up research project iteration through a strong technical vision that included Metaflow for flexible compute and Python/C++ bindings for backtest simulation.
- Introduced management standards, starting with fortnightly 1-1s, monthly managerial catchups, weekly research presentations and an explicit career ladder.


### Senior Research Engineer, Dec 2018 - July 2019
*Technology Incubation, Dolby Laboratories, Sydney*

- Developing SOTA speech recognition technology for use with Dolby devices and services.
- Slashed training time from a 5 days to 30 minutes by porting Julia Deep Learning codebase to CUDA including an implementation of CTC loss. This enabled more complex model builds and faster experimentation which yielded 95% detection with low false positive rates.
- Championed separation of training and deployment code to allow for greater flexibility, in recognition of differing constraints and requirements for each task.
- Determined the relationship between Baum Welch and CTC to educate colleagues and guided efforts for multi-accent training with mixed corpora. 


### Operations Research Analyst, Jan 2016 - Apr 2018
*Hudson River Trading, Singapore*

 - Improving trading control AI’s decision making processes with machine learning
 - Reduced FPGA downtime from 10 min to 1 min by training a pricing model to assess impact to PNL and a system to automatically handle failure, improving PNL by 1%.
 - Initiated metadata collection of AI  jobs and processes and developed system to automatically analyse failures to effectively direct improvements.
 - Rebuilt the automated Corporate Actions system while improving speed, accuracy and robustness, allowing automated trading to take advantage of the volatility surrounding CAs.
 - Achieved consensus among team to develop new style guide with an increased line length and spearheaded documentation efforts to reduce technical debt.


### Data Scientist, Oct 2018 - Dec 2018
*Sen. Di Natale's Office (Australian Greens), Australian Parliament*

 - Built ordinal LASSO logistic models to quantify odds ratios of various demographic indicators on survey responses, informing childcare, health and education policy development.
 - Educated key stakeholders on the capabilities of Data Science, leading to more trust and reliance in data science methods when developing policy and campaign strategy.
 - Founded a volunteer Data Science group to provide data science manpower to party leadership and set up longer term projects based on census and voter contact data.



## TALKS

- [GPU Acceleration with CUDA and Python](https://github.com/nayyarv/PyCudaIntro) | [Event Link](https://www.meetup.com/sydneypython/events/nrphrpyzcbpc/) - Talk presented at Sydney Python August 2018 about CUDA architecture and development
    - Upcoming presentation at PyCON AU 2019, Science and Data stream.

- [Hacking Binary Ops in CPython](https://github.com/nayyarv/CpythonLookingGlass) | [Event Link](https://www.meetup.com/sydneypython/events/nrphrpyxkbjc/) - Talk presented at Sydney Python January 2019

- [The What, Why and How of Bayesian Inference](https://docs.google.com/presentation/d/e/2PACX-1vSykBSh072plEpk61jQvznUdNzS6MCpNYPltzDmxr4A0AOCkFVTtJfK3UqusuCDwParywF7sPwemIds/pub?start=false&loop=false&delayms=3000) | [Video](https://www.youtube.com/watch?v=A9r8C2GFR4k) | [Event Link](https://www.meetup.com/Data-Science-Sydney/events/259627528/) - presented to Sydney Data Science, March 2019

- [inteRnals](https://github.com/nayyarv/inteRnals) | [Event Link](https://www.meetup.com/R-Users-Sydney/events/260866643/) - advanced look at GNU R, presented at Sydney Users of R, May 2019.

- [Bayesian Modelling with Tensorflow Probability](https://github.com/nayyarv/ProbablyTensorFlow) | [Event Link](https://www.meetup.com/en-AU/DeepSchool-io/events/260753939/) - Introduction to Bayesian Linear Models with TFP.

- [DSAi Rethinking](https://dsai.org.au/courses/01-dsai-study-bayesian-inference-statistical-rethinking/) - Ran 5 week Bayesian Rethinking Study Group, April-May 2019



## OPEN SOURCE

 - [Numpy Contribution PR #6029](https://github.com/numpy/numpy/pull/6029) - Automatic number of bins for `np.histogram`, released in numpy v1.11. Major fixes in [#6288](https://github.com/numpy/numpy/pull/6288)/[#7243](https://github.com/numpy/numpy/pull/7243) and minor fixes in [#10739](https://github.com/numpy/numpy/pull/10739) and support in issue trackers.
 - [Abstract Syntax Tree Tail Recursion](https://github.com/nayyarv/python-tailrec) - AST manipulation in Python to optimise a tail recursive call into a loop.
 - [Rethinking PR #152](https://github.com/rmcelreath/rethinking/pull/152) - adding tidyverse compatibility with improved inheritance checking to the `rethinking` library.


## EDUCATION

### BEng(Electrical, Honours) & BSci(Statistics, Honours)
*UNSW 2010-2015*

 - Faculty of Engineering Dean’s Award (Top 2% in cohort) — 2011,12,13,14
 - Faculty of Science Research Scholarship, $3800.
 - International Student Exchange Scholarship, $5000 - University of California SD
 - High Distinction Average (87.2)

### Thesis - Engineering (2014)
*Machine Learning, Honours/Masters Year*

- Developed novel technique for emotion recognition by applying Bayesian Inference to GMMs. Technique was more robust when tested on IEMOCAP and LDC corpuses.
- Researched and developed MCMC algorithms for use in high dimension spaces with automated 
- Implemented expensive likelihood evaluation in CUDA and interfaced it to Python. [Github]
(https://github.com/nayyarv/MonteGMM)

### Thesis - Statstics (2015)
*Bayesian Inference, Honours/Masters Year*

- Proposed novel sampling scheme to handle contamination models with expensive likelihoods using Approximate Bayesian Computations (ABCs).
- Proved performance on simplified population datasets with R.
- Derived error bounds and theoretical ROC curves of the sampling method.


## BLOG ARTICLES

- [Bayesian GPS](https://nayyarv.github.io/blog/bayesian-gps) - A Bayesian take on a simplified GPS problem.
- [Reinforcement Learning](https://nayyarv.github.io/blog/cartpole-q-learning) - Neural Q Learning applied to OpenAi Cartpole.
- [Tosser](https://nayyarv.github.io/blog/tosser) - How to play a game with E(X) -> infinity, while p(X>0) -> 0.
- [Contributing to Numpy](https://nayyarv.github.io/blog/my-contribution-to-numpy) - about my PR referenced above.

## SKILLS
For the ATS systems out there

- Clustering - GMMs, KMeans, Spectral Clustering, DBScan
- Classification - Bagging, Boosting (Catboost, XGBoost), SVMs
- Bayesian Inference - MCMC (Stan), Variational Bayes (BayesPy), pyro, edward
- Neural Networks / Deep Learning - tensorflow, pytorch, keras [(blog post)](https://nayyarv.github.io/blog/a-bayesians-view-on-neural-nets)
- Regression - LASSO, Ridge, ordinal logistic, multinomial, GLMs
- Dimensionality Reduction - PCA, Autoencoders 
- Reinforcement Learning - Q learning, policy gradients, actor critic
- Databases - SQL (Postgres, MySQL), NoSQL (Redis, Mongo)
- Programming - Python, R, C, CUDA, Julia, Haskell
- Deployment Analytics - Bandit Methods, A/B/n testing [(blog post)](https://nayyarv.github.io/blog/ab-testing-bandit-methods)
- Distributed Programming - Sched (HRT), Spark


## ADDITIONAL EXPERIENCE

### Machine Learning Consultant, Sep 2019 - Dec 2019

*Safety in Numbers, http://54f37y.com/*

- Developed the ML strategy for the company and formalised guidelines on data needs and labelling strategies for training image recognition algorithms.
- Slashed human labelling time by developing a W-beam Neural Net classifier to automatically tag video times and bootstrap the dataset size for next gen products.

### Data Scientist, Apr 2015 - Aug 2015
*Learning and Teaching Unit, UNSW*

- Discovered at-risk students by using unsupervised clustering on test behaviour.
- Analysed course comments using NLP to identify poorly received modules.

### R&D Engineer, Jan 2015 - Mar 2015
*Buildings Alive*

- Startup developing innovative modelling to increase energy efficiency in offices
- Slashed manpower costs and R&D deployment time by moving development to python and integrating with existing Java frontend using protocol buffers.
- Championed sensor scraping system to augment energy modelling by deploying Raspberry Pis running sMAP to contracted office buildings. 

### DSP Research Intern, Dec 2012 - Feb 2013
*Digital Signal Processing, Cochlear*

- Trained Neural Response models on 200,000 measurements and fed into Classification Tree  to allow for automated calibration of Cochlear Implant.
- Raised accuracy and speed of algorithm by 25% while improving robustness.

