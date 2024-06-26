---
author: chrisbeeley
categories:
- Uncategorized
date: "2021-03-26T10:43:42Z"
title: SQL versus analytic tools
---

From a [tweet from my NHS-R buddy John MacKintosh](https://twitter.com/_johnmackintosh/status/1374986918878965760?s=19)

“Two schools of thought :  
1\. Do as much as possible using SQL (joins/ munging/ calculations and analysis) so that your analysis is portable between different BI / Viz tools  
2\. Do the basics (e.g. joins and simple aggregates) in SQL, calcs and analysis in front end tools”

This is a great question, and I don’t mean to detract from its greatness when I say it is over simplistic. It’s an important question, and I have a lot to say on the subject, so much so in fact that I’m going to answer a tweet with a blog, which is very on brand for me 😄.When we think of data scientists and data engineers, we tend to think of data engineers providing beautifully normal and rapid data structures and data scientists wrangling them with a mix of SQL and R/ Python/ whatever. But in my experience it doesn’t really work cleanly that way, and nor should it.

An important factor is the way that the data is organised and documented. People in the NHS often get upset about all the different datasets that we use. A common complaint is that they don’t link up easily. People who don’t work in data think that the Trust has this big database of everything, and you just go and look up the thing you’re interested in, and it’s right there indexed against every other piece of data, and off you go. This notion is hilarious to anyone to anybody who actually works with data.

It’s not because the data is bad or because it’s not being looked after properly. It seems to me that databases, far from being perfect platonic ideas about the trust are in fact opinionated. You tend to find that they do the thing that they were originally designed to do very well. The payroll database is really good at paying people. The EHR is really good at, well, being an EHR. Data scientists, by our very nature, always want to do something that the database was not designed to do. That almost seems to me to be an actual definition of data science. Taking a database and making it do something else. If your database has already done what you’re doing, chances are you don’t need a data scientist. Just stick one of those auto ML things on it or point PowerBI at the cube. Boom. Instant insight.

So what does this all mean for the question? It means that the data engineers and data scientists are on the same team. They’re not just throwing stuff over the wall at each other. The data scientists are customers of the data engineers, and we couldn’t do a thing without them, but we can be smart customers. We might want the data in a different form, sure. We might prefer it if some of the joins were done in the backend to save us a bit of work and to help us all work together. But we can give stuff back. We might use an algorithm to predict the risk of rehospitalisation at 28 days, say. Once we’ve done that we can probably use that calculated value more quickly if it’s productionised in the DB. And if it is productionised in the DB that means everyone can access it- not just the data scientists but also the data engineers and all of their customers.

Data scientists and data engineers working together can take a database that does one thing and turn it into a database that does two things. And they can turn that database into something that does three things. And the whole time the data engineers are keeping it all fast, scalable, legible, and accurate. It’s early days for us, working this way. I’ve read about it many times, but we’re working with our friends in data engineering and I hope one day to tell our story and how we’ve all worked together to produce lots of insights and delivered them all around the Trust.

To answer the question, then, I would say that if you want to go fast, use analytic based tools, and if you want to go together take the time to port all of the insight to SQL based tools. And given the state of analytics in the NHS as it stands today I would recommend we all go as fast and as together as possible. I know we at Nottinghamshire Healthcare are.