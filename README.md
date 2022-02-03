# AtoIFTTT

AtoIFTTT is short for "Alexa to If-this-then-that"; it's a simple [AWS Lambda] that packages up an [Alexa Skills Kit] Intent along with up to three "slot" values and sends them via a Web Request as an input to a "recipe" using the IFTTT [Maker Channel].

## Why IFTTT?
This approach is convenient for two major reasons :

1. It allows for rapid prototyping of Alexa Skills using only modifications to the Intent Model on the front end and IFTTT recipes on the backend.
2. It opens up any IFTTT Channel with a Action on it as a potential "tool" for Alexa. 

## Getting Started with AtoIFTTT
(Note: If you haven't created an Alexa Skills Kit Lambda before, it's best to read "[Developing an Alexa Skill as a Lambda Function]" first to familiarize yourself with the process. You should also be familiar with the basic workings of [IFTTT])

1. If you aren't already a member, [join] IFTTT.
2. Enable the [Maker Channel] on your account.
3. When you view the Maker Channel in your account, you'll see a string labeled "Your secret key is:".  Note this string and save it for step 5.
4. Using the code in "AtoIFTTT.js", follow the instructions for [Creating a Lambda Function for an Alexa Skill], using the "AtoIFTTT.js" code rather than the template code.
5. Near the top of the file, find the string "INSERT_YOUR_MAKER_KEY_HERE". Replace this string with your private key from step 3.
6. Follow the remaining steps to finish creating the Lambda function and, most importantly, assigning a basic execution Role in order to allow the Alexa skill to make use of the Lambda.
7. Once you've saved the Lambda and go back to the "Function List" page, you'll see your Lambda listed and below it, the label "Function ARN" followed by a string starting with "arn:" (e.g., "arn:aws:lambda:us-east-1:201599999999:function:Function-Name".  Take note of this as you'll need it to tell your Alexa Skill what function to call.

That's it!  You're now ready to use IFTTT with Alexa! However, you'll probably benefit from a couple of examples of how to use IFTTT to prototype new Alexa Skills... if so, read on.

## Examples
Two examples are included that make use of the schema in IntentSchema.json and SampleUtterances.txt - a "Find My Phone" command and a "Send a Text" command.  In order to use these, though, you'll need to do the following :

1. Enable the [Phone Call Channel] on your IFTTT account.  This will set up IFTTT to call your phone as part of the "Find My Phone" command.
2. Enable the [SMS Channel] on your IFTTT account.  This will set up IFTTT to send text messages to your phone as part of the "Send a Text" command.
3. Create an instance of the [Alexa "FindMyPhoneIntent"] Recipe.  For the "Event Name", be sure to use "FindMyPhoneIntent" (the reason for this will become apparent when you see the Intent Schema.
4. Create an instance of the [Alexa "TextIntent"] Recipe.  For the "Event Name" be sure to specify "TextIntent".
5. Back in the Amazon Developer Console, follow the steps under [Testing a Lambda Function with an Echo], but use the IntentSchema.json from this project for the Intent Schema, and the contents of "SampleUtterances.txt" for the Sample Utterances.
6. Give your Skill a simple name like "Maker". 

Now you're good to go - say "Alexa" (or whatever your Echo trigger phrase is) "Launch Maker" (or whichever name you assigned to the Skill), and Echo will prompt you to say a command.  If you say "Find my phone", you should hear a confirmation prompt (this comes from IFTTT), followed by your phone ringing.  Similarly, if you say "Send the message Where are you"), this should be sent to your phone as a text.

That's about it... play around with the Utterances, add your own intents... or just use the Lambda code as an example of how to send web requests using Alexa. Contact me via https://markfogle.com with any questions or comments.

[join]:https://ifttt.com/join
[AWS Lambda]:http://aws.amazon.com/lambda
[Alexa Skills Kit]:https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit
[Maker Channel]:https://ifttt.com/maker
[Developing an Alexa Skill as a Lambda Function]:https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-lambda-function
[IFTTT]:https://www.ifttt.com
[Creating a Lambda Function for an Alexa Skill]:https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-lambda-function#Creating%20a%20Lambda%20Function%20for%20an%20Alexa%20Skill
[Phone Call Channel]:https://ifttt.com/phone_call
[SMS Channel]:https://ifttt.com/sms
[Alexa "FindMyPhoneIntent"]:https://ifttt.com/recipes/304080-alexa-findmyphoneintent
[Alexa "TextIntent"]:https://ifttt.com/recipes/304081-alexa-textintent
[Testing a Lambda Function with an Echo]:https://developer.amazon.com/public/solutions/alexa/alexa-skills-kit/docs/developing-an-alexa-skill-as-a-lambda-function#Testing%20a%20Lambda%20Function%20with%20an%20Echo

