# twitter_name_changer
### Overview
This is a Python program for automatic name Changer bot based on Twitter. Generally, this program works until the local Python software/Online Python Notebook is running. So a system can be developed based on 
Online platform HEROKU, wherein the code can be deployed and the Twitter bot works even if the local python software is not running.

### CODE AND IT’S EXPLANATION 
The code consists of three files that have to be uploaded on GitHub.
I) Procfile
II) mainbot.py
III) requirements.txt

The codes and explanations for respective files are as below:
I) Procfile

`worker: python mainbot.py`
It is used connect our GitHub code to Heroku. Here the second word
is the language in which the code is written and the third one is the
the name of the file that contains the code.

II) mainbot.py

`import tweepy`

It is a python library to access the twitter API.

`import os`

It is the operating system library which is used to access operating
system dependent functionality.

Now a function has been defined below:

`def create_api():`

`consumer_key = os.getenv('consumer_key')`

`consumer_secret = os.getenv('consumer_secret')`

`access_token = os.getenv('access_token')`

`access_token_secret = os.getenv('access_token_secret')`

The above lines are keys and tokens which are used to take our
required personal information from twitter.

`auth = tweepy.OAuthHandler(consumer_key,consumer_secret)`

Here we are creating an instance of OAuthHandler.

`auth.set_access_token(access_token, access_token_secret)`

Here we are setting the access so that the tokens can be used.

`api = tweepy.API(auth,wait_on_rate_limit=True,wait_on_rate_limit_notify = True)`

`api.verify_credentials()`

`print('API Created')`

`return api`

Here we finally authenticate to twitter and verify the
credentials and with returning the api the function definition ends.

`import time`

Here we import time module for time operations

Now a function has been defined below:


`def follower_count(user):`

    emoji_numbers = {0: "0️⃣ ", 1: "1️⃣ ", 2: "2️⃣ ", 3: "3️⃣ ", 4: "4️⃣ ", 5: "5️⃣ ", 6: "6️⃣ ", 7: "7️⃣ ", 8: "8️⃣ ", 9: "9️⃣ "}`
    
This line sets the emojis for respective digits which will be used
to display in your name.

    `uf_split = [int(i) for i in str(user.followers_count)]`

The above line is used to separate the characters in the string.

    `emoji_followers = ''.join([emoji_numbers[j] for j in uf_split if j in emoji_numbers.keys()])`
    
    `return emoji_followers`
    
By above lines the characters are joined together and
emoji_followers is returned and hence function definition ends.

`api = create_api()`

api is created by the above line as the function name clearly
suggests.

`while True:`

     `user = api.get_user('PiyushK09474018')api.update_profile(name=f'Piyush Kumar|{follower_count(user)} Followers')`

    `print(f'Updating Twitter Name : Piyush Kumar|{follower_count(user)} Followers')`
    
    `print('Waiting to refresh')`
    
    `time.sleep(60)`
    
    
The above while loop takes user name to access the account then
update the name according the number of followers the user has.
Then it prints the updated name. Now “time.sleep()” is a function
that is used to add delay in the execution of the program.

III) requirements.txt

`tweepy`

As mentioned earlier, it is a python library to access the twitter API.

### Deployment

* We have to make a twitter developer account and create an app
there and then from keys and tokens section we have to generate
the keys and use them in code in case we are running the
program into google colab.
* We have to make an account on Heroku. Connect our GitHub with
Heroku and the respective repository that contains the code.
Then in the settings section, we have to add our tokens and keys
that we get from our twitter developer account. Also, we have to
edit in Dynos which is in Resources section. Then we can check
from Activity section that whether the build and deployment is
done or not.
