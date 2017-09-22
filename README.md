# OrangeBot

## What is OrangeBot? 

Twitter bot that responds to positive and negative feedback on Twitter relating to keyword "homedepot". 

OrangeBot uses:
  - Language: javascript, framework: node
  - "twit" (a Twitter API client for node
  - IBM Watson Tone Analyzer API
  - Nodemailer API
  
## How does it work?

OrangeBot uses the Twitter API to scan and retrieve tweets that contain the keyword "homedepot". 

The tweet is stored and sent through the Tone Analyzer which uses linguistic analysis to detect the emotional tone of the written text. 

The five emotions that the analyzer detects are anger, disgust, fear, joy, and sadness. The tone analyzer will then give a score to each of these emotions e.g. someone tweets, "I hate homedepot!". It would evaluate the anger value to be .78 which infers that the tweeter is expressing significant anger. 

Finally, the bot will calculate a weighted average of the five values and produce a score. If the average is greater than .25, a email will be sent to a Home Depot employee using the nodemailer API. However, if the average is less than .25, the bot will reply to the account from which the tweet originated prompting the user to give Home Depot a review.

## Why is this useful?

This allows the buisness to monitor their customer service and respond according to their customers compliments or complaints.

## How to Use

Before you start

Make sure you have a Twitter Account and its access/consumer keys. You can replace the keys in config.js with your own keys.
Same with analyzer.js. The current access key only has 2500 calls minus whatever we already used.

You can get your keys at:
    
```    
https://apps.twitter.com/
```

```
https://console.bluemix.net/registration/?target=/catalog/%3fcategory=watson&cm_mmc=Earned-_-Watson+Core+-+Platform-_-WW_WW-_-intercom&cm_mmca1=000000OF&cm_mmca2=10000409& 
```

Also make sure you have set up two email accounts. One for the bot and the other as a test employee. Go to index.js and find the nodemailer section and change the user and password to those of the emails you will be using. 

And you're all set!
    
1. Create a folder.
3. Change the directory to the folder you just created. For example:
  
    ```
    cd User/Chame/Desktop/orangebot
    git clone https://github.com/chamewin/orangebot
    ```
    
4. Install all necessary npm packages. 

    ```
    npm install
    npm install twit --save
    npm install watson-developer-cloud --save
    npm install nodemailer --save
    ```
    
5. Run command
    
    ```
    node index.js
    ```
   
## Issues

The tone analyzer api only allows 2500 uses. You can get more at IBM Bluemix.

Twitter won't allow repeated requests using the current code. Our code pulls from Twitter every 30 secs, but it only pulls
the lastest post. I plan on fixing this later by changing to "twit's" stream function from its get function. 

Sometimes the post will be neutral and will not return anything.

Credits: Kyle Xiao, James Nguyen, Benson Yang, Annie Lian

