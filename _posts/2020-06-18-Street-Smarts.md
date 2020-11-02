---
layout: post
title: Street Smarts
subtitle: Compare cars' specs, including CO2 emissions, in under a minute!
image: https://github.com/JonNData/JonNData.github.io/blob/master/img/StreetSmarts06-18.jpg?raw=true
tags: [AWS, Fast API, SQL, predictive, data analysis, car, craigslist]
---
Visit our site at:  
[https://www.streetsmarts.online/](https://www.streetsmarts.online/)  
![streetsmarts_demo](https://media.giphy.com/media/fw8hWPw7M7jsvtq1QN/giphy.gif)

During a two month period I worked on a team as a data scientist and data engineer to produce Street Smarts. I helped launch a website that allows the user to interact with car data in meaningful ways. 

In this post I will cover my endeavors regarding:
* Understanding the product vision
* Researching possibilities
* Exploring data
* Building a basic API with Flask and Heroku
* Implementing a more sophisticated  approach with Fast API and AWS
* Teamwork and reflection
### Finding Direction
Our project was essentially greenfield, starting from scratch. The previous team that worked on code before us didn't have any deliverables to bequeath nor did they nail down 
the objectives they set. This was a blessing, but required strong communication to hone our goals. The product vision document had some scattered amalgamation of car information 
as a service, but no clear identity was given to the product. After meeting with the stakeholder, we were given more questions than answers, yet it was exciting to flesh out the unknown. 

The team consisted of web, backend, and data science groups. Data science naturally drove the direction that the project could take; it was up to us to see what information was out there and what we could bring together as a service. After scouring several datasets and performing some exploratory analysis, what ended up catching our eye was a dataset from the [EPA](https://www.fueleconomy.gov/feg/download.shtml) that contained car information dating back to 1984.

After some quick data [exploration](https://colab.research.google.com/drive/13O_SfTh_9WDlecc34B9u2Xmnb4URd6AK?usp=sharing) we decided this dataset was ideal for providing us car emissions in the form of CO<sub>2</sub> in grams per mile. This would give us a unique spin for our website, because all other major car listing websites neglected to inform the environmental impact directly. 

### A Pricey Challenge
However, there was a tradeoff that we reached when choosing this as our main dataset: it didn't include price information. Nowadays, retail car information isn't as freely accessible as it used to be. APIs from edmunds.com or cars.com can cost several dollars per query, and that would quickly add up on a free web app. We scoured many other datasets and experimented with scraping, and we found a comprehensive listing of car prices in a Craigslist dataset that contained 430,000+ cars. Now we had data that we could model price from, but there was a key challenge that we faced: matching the car model naming conventions. While the EPA dataset might list the model name as `Range Rover Evoque Cabriolet`, the craigslist set would just have it as `evoque`. The user would need to make just one query into our database so we had to come up with a way to either merge/join these datasets or translate between them.  

We found our way to Rapid Fuzz, a python library that uses Levenshtein distance. This distance measures how many edits it takes to convert one string to the other. Using this we were able to explore and model on the Craigslist dataset normally, and translate the EPA-based query to something our predictive model would expect.

### A Minimum Viable Product
Our first objective as data scientists was to get endpoints for the rest of our team to work with. To this end, we very quickly inserted data into a SQL database and set up dummy endpoints via a Flask app. This was quick and easy to setup using the `psycopg` library using python. Specifically, our dummy endpoints only needed to take in car spec inputs such as odometer and mileage in a `POST` request, perform some arbitrary calculation, and return the 'prediction.' We pushed our backend up to Heroku using continuous deployment and linking to Github to automatically show changes made to our repository.

I believe our focused efforts on pushing out something that was attainable and meets the minimum requirements ASAP was key to our team's success. Getting things done right out of the gate kept the team motivated and always looking toward solutions. This fast progress was also what drove our efficient agile development; pushing to achieve workable results ASAP gave us enough time to look forward and realize what we could achieve.

### Iterating Improvements
Once we had set up the team with the bare minimums to proceed, it was time to enhance the machine learning pipeline. We took some time to evaluate different random forest models, XGBoost, and neural networks. Mean absolute error was prioritized over R-squared because it gave a us a more direct metric over different models. See the shortcomings of R-squared for non-linear models [here](https://statisticsbyjim.com/regression/r-squared-invalid-nonlinear-regression/).

On the data science side we all wear the engineering and analyst hats, but my particular strengths have been the implementation of ideas.   
My XGBoost predictive model had the best scores of the team.
I wrote a function to solve the complex merge between EPA and craigslist datasets.

I monitor the billing charges and keep the team notified when we are projected over budget by setting up a CloudWatch alarm
 
 
I independently test our apps to troubleshoot any issues we couldn’t solve together and ensure I sufficiently understand what we did. Here is a repository that I made
 
My  data preprocessing steps transformed the data in the most valuable way  
Since I am taking a AWS course concurrently, I think my familiarity with AWS has been a good asset. I’ve tracked EC2 instances alongside our elastic beanstalk creations, as well as kept the S3 buckets in mind  
 
I co-wrote the code to fetch car_images and return working links, then I refactored it heavily to be more programmatic and easier to read.  
 
I guided general command line use with virtual environments and git usage  
 
What are some of your weaknesses as a member of your team? How have you worked to overcome some of your individual weaknesses? Be specific.  

Object oriented programming mindset  

Following mikio’s example I implemented it in the rest of our functions and app  
Pytest  
Researched and watched videos to learn  
Describe a teamwork problem that you as a team have had to overcome. How did you contribute to the problem itself? How did you contribute to the solution to the problem? Be specific.  
Total group involvement. Some members need encouragement to speak out  
At times, to move things along I just cut to the point. There may or may not be instances in which a longer silence would produce input from others  
Sometimes I’ll ask for input from people that haven’t spoken up  
How is your team measuring the success of your product? How do you know you are solving user problems? How are you using these measurements to inform what to build next?  
As a team we measure our success by the continued bewilderment of management in response to our progression speed.  
 
 
 
In terms of users, we have measured the time it takes to do car comparison tasks on the major car websites  
I have distributed the site for review and submitted responses  
  
ORM sqlalchemy, technologies used , link personal fork. GIF

Outline:
Gif  
Intro  
* pvd, greenfield, team members.  
Data  
* epa
* private api, costs
* CL, truecar, carspecs
First iteration, RC1  
* motivation 
* PaaS Heroku flask insert DB
RC2  
* IaaS Fast RDS EB
* modeling, costs of size, progress chart, error metric choice, R^2 adjusted
INPUT OUTPUT Feature building for intuition  
Communicating with web and backend  
limitations and looking ahead  

