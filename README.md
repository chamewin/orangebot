# orangebot

What is OrangeBot? 

Twitter bot that responds to positive and negative feedback on Twitter relating to keyword "homedepot". 

OrangeBot uses:
  - Language: javascript, framework: node
  - "twit" (a Twitter API client for node
  - IBM Watson Tone Analyzer API
  - Nodemailer API
  
How does it work?

OrangeBot uses the Twitter API to scan and retrieve tweets that contain the keyword "homedepot". The tweet is stored and sent 
through the Tone Analyzer which uses linguistic analysis to detect the emotional tone of the written text. The five emotions 
that the analyzer detects are anger, disgust, fear, joy, and sadness. The tone analyzer will then give a score to each of 
these emotions e.g. someone tweets, "I hate homedepot!". It would evaluate the anger value to be .78 which infers that the 
tweeter is expressing significant anger. Finally, the bot will calculate a weighted average of the five values and produce a 
score. If the average is greater than .25, a email will be sent to a Home Depot employee using the nodemailer API. However, if 
the average is less than .25, the bot will reply to the account from which the tweet originated prompting the user to give 
Home Depot a review.

Why is this useful?

This allows the buisness to monitor their customer service and respond according to their customers compliments or complaints.

How to Use

1. Clone this repo to your computer. 
2. Open terminal.
3. Change the directory to where the files you cloned are.
4. Install all necessary npm packages. 
  - npm install twit --save
  - npm install watson-developer-cloud --save
  - npm install nodemailer --save
5. Run with command "node index.js"

Credits: Kyle Xiao, James Nguyen, Benson Yang, Annie Lian

Version 0
