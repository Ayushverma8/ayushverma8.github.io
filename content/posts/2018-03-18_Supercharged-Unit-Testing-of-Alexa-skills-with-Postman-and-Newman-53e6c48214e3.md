---
author:
  name: "Ayush Verma"
date: 2018-03-08
linktitle: Supercharged Unit Testing of Alexa skills with Postman and Newman
type:
- post
- posts
title: Supercharged Unit Testing of Alexa skills with Postman and Newman
weight: 10
series:
- Cloud
---


Testing Alexa Skill with Postman supersedes the basic testing service provided by the Amazon Developer Portal and Tools.

Lately Amazon has been working on improving the developer experience for its Alexa intelligent personal assistant. Part of this strategy Skill Management API,provides the ability to test multi-turn…

![](https://cdn-images-1.medium.com/max/800/1*9cVPQ8azohAoaMvopR-ESw.png)

Lately Amazon has been working on improving the developer experience for its Alexa intelligent personal assistant. Part of this strategy Skill Management [API](https://hackernoon.com/tagged/api),provides the ability to test multi-turn conversation, entity resolution, dialog management, and more features that are not supported by existing test tools.

Testing Alexa Skill with Postman supersedes the basic testing service provided by the Amazon Developer Portal.

To start, we are going to use three things to make all of this work

We need threee things to get started

*   [AWS Lambda](https://docs.aws.amazon.com/lambda/latest/dg/welcome.html)

If you haven’t built a skill for Alexa before, I would suggest , go through [Build skill in 5 minutes](https://developer.amazon.com/alexa-skills-kit/alexa-skill-quick-start-tutorial) and get started with core principles .

Once you gotten your Lambda function set up and running we are good to go .

![Function might be looking something like this](https://cdn-images-1.medium.com/max/800/1*Mjp8Lt9yv40yDG4OWAEo1g.png)
Function might be looking something like this

*   [API Gateway](https://aws.amazon.com/api-gateway/)

With Amazon API Gateway, we can provide Alexa with a consistent and scalable programming interface to access endpoints in the backend.

1.  To begin with , go to [AWS API Gateway](https://aws.amazon.com/api-gateway/) and sign in to the console.
2.  First, make sure that you have chosen “New API” from the radio buttons at the top of the page.Then make a new role and choose “L[ambda execution role](https://www.google.co.in/search?q=lambda%20execution%20role%20cloudformation&ved=0ahUKEwjAntrtwvXZAhWLfZAKHT4ZCwEQsKwBCC0oADAA)”
3.  Now you need to open the Actions button, and this time choose “Deploy API.” In the Deploy API box that appears, choose “\[New Stage\]” for Deployment/Test stage. For the other three values (Stage Name, Stage description, and Deployment description), you can just use the word “Test” for all of them. The values don’t matter, it’s just so that you know what the purpose of this new API is for.We gonna need this at later stage.

![Sample Dashboard](https://cdn-images-1.medium.com/max/800/1*3I6gwmZt-Tx0Ey2yJJl79g.png)
Sample Dashboard

4.Now Now , Copy the Invoke URL from the blue box at the top of the screen. Your API is set up and ready to roll.

*   Getting up and running with Postman API Tool

1.  If you don’t already have this Amazing tool, make sure to download [Postman](https://www.getpostman.com/). but wait …

**Why Postman ?**

*   In this article , We will be using Postman to create and execute our unit tests against our Lambda function.Each time that you make a change to your Lambda, you should run your tests to make sure that everything is still working as expected
*   We have something Amazing called [Monitors](https://www.getpostman.com/docs/v6/postman/monitors/intro_monitors) , Which will help us to save overhead in Unittesting [Alexa Skills](https://hackernoon.com/tagged/alexa-skills) .
*   Postman helps us writing pre-request scripts and test scripts for requests , based on TDD. and hell yeah , [_Postman collections_](https://www.getpostman.com/docs/v6/postman/scripts/postman_sandbox) are Making API testing great again.
*   I work at Postman. 😜

Alright , So now you are up and running Postman hopefully.

If you need more security for each requests over API gateway then you can add [AWS Signatures](https://docs.aws.amazon.com/apigateway/latest/developerguide/how-to-use-postman-to-call-api.html) and Proceed.

![](https://cdn-images-1.medium.com/max/800/1*AoXZaCpNFmXBKHHdBKJqvQ.png)

Now you need a sample request get started with testing. You can get a Lambda request from the Service Simulator like serverless , or from your Cloudwatch logs in amazon account.

Choose body and click on “raw” radio button , which indicates we are forwarding our own JSON data to Lambda.

![Raw datatype](https://cdn-images-1.medium.com/max/800/1*DqDfwXo5Lqeknwd49dxNTg.png)
Raw datatype

Output will be embdded `"SSML"`: Indicates that the output speech is text [marked up with SSML](https://developer.amazon.com/docs/custom-skills/speech-synthesis-markup-language-ssml-reference.html). It’s a way by which alexa communicates.

You can know more about Request structure [here](https://developer.amazon.com/docs/smapi/account-linking-schemas.html).

At this point be sure and verified that you can successfully communicate with your Lambda, Now we can start creating a suite of tests for this request which will define units .

For Example , We are using favorite color skill, “`WhatsMyColorIntent what my favorite color”` should return “`orange"`

pm.test("Body is correct", function () {  
    pm.response.to.have.body("orange");  
});

Similary when you want to check if Alexa continues the skill after user gives a response and reprompts for input , We need to check field `shouldEndSession`

![Tests](https://cdn-images-1.medium.com/max/800/1*1w0Jdms73tJlX-bvMRuykQ.png)
Tests

Similarly you can define set of tests for a Alexa Skill and run it everytime you make some changes in skill. Postman will help you to know breaks when you make any unexpected change in the request or code.

This way you save much of time and spend writing code instead of boring testing.

You can also save Alexa response to Postman and write test without calling Prod API again again for one session.You can learn more [here](http://blog.getpostman.com/2017/03/16/simulate-a-back-end-with-postmans-mock-service/). You can run your collection in Runner and Know status of your Skill.

![Monitor Skills on Postman’s cloud.](https://cdn-images-1.medium.com/max/800/1*M6mtjD-HKQYi_ZjHkLmDgQ.png)
Monitor Skills on Postman’s cloud.

Now ,If you are CLI freak like me , you would prefer testing all of Tests from Command Line right ?

No problem , Postman has a tool called , [newman](https://github.com/postmanlabs/newman) , it’s a command line companion for Postman.

Install newman by `npm install newman --global` with NodeJS.

That’s it. Now it’s time to get hands dirty with Collections in CLI.

![Export by clicking here.](https://cdn-images-1.medium.com/max/800/1*5jfhpJ8RpzJEs6eBqIuX2w.png)
Export by clicking here.

Now , Run your tests in CLI with

`newman run AlexaSkillTesting/test_to_check_color.json`

And That’s it. See your terminal talking to Postman and Testing for you .

And Yes , **Postman Monitors can surely help by keeping an eyes on response and notifies when something goes wrong. Because , We’re going to write an entire suite of unit tests for our skill so that when we make a change to something, we have the confidence that nothing has broken and Everything is 200 OK . And It Absolutely helps us in functional testing of Skill at each conversational phase. So , Cheers 🍺**

Hopefully , I have helped you in testing alexa skills . Thanks for reading 🙌

By [Ayush Verma](https://medium.com/@Ayushverma8) on [March 18, 2018](https://medium.com/p/53e6c48214e3).

[Canonical link](https://medium.com/@Ayushverma8/supercharged-unit-testing-of-alexa-skills-with-postman-and-newman-53e6c48214e3)

Exported from [Medium](https://medium.com) on July 6, 2019.