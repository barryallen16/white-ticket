### TicketNew Automatic Ticket booking bot
This is a selenium automation project i did 3 years ago, ie on 2023. I primarly made this ticket booking bot for booking tickets for the movie 'leo' starring vijay, directed by lokesh kanagaraj. The movie's hype was so big, everyone thought if we did rush to get the tickets, our movie experience would be spoiled by all the internet spoiler and meme pages.

- The code is amuatuer in itself.
- There are lot of if clauses. 
- everything is hardcoded from the desired theatre name, show timings, specific seat selection (which changed from theatre to theatre)
- even i placed the telegram bot api key hardcoded in the code. I would have ofcourse removed it by the time you read this.
- the library i need while developing has been updated or not available. i didnt freeze a requirements.txt . so no luck making this code work without rewrite. but we can just remove the telegram logic of the code, the booking automation would still work as intended. 
-  telegram bot is just for sending updates in telegram group chat.
- This code even though bad in some sense. feels nostalgic and makes me realize how far i have come.

## Working
at the time of 2023, paytm was using ticketnew as its movie booking service. The ticket booking process goes like this:
- you enter your phone number and get a otp.
- after entering the otp, you are allowed to select and book ticket. 
- when payment is initailized for booking the ticket, a payment request is sent to the corresponding paytm account of the phone number we logged in with. 
- you can just make payment in paytm app. and your ticket is booked.

## Automation workflow
- i used selenium to enter the hardcoded phone number, once i get the otp i enter it in terminal. the otp is captured by the input method.
- next the script refreshes the page every 30 seconds to see if any of the theatre names in the desired list of theatre name is available for booking. 
- if the theatre is available, then the specific show timings is searched for in that theatre, (we couldn't get permission to see night show)
- i had set up a telegram bot to send updates in a telegram group. so that we , friends stay updated on whats happening. like if a desired theatre has open, show timing is available. 
- then specific seat are seating, i was booking ticket for 10 friends, myself included. everyone told that they preferred the center row seats best. but it is ok if we get corner seats too.
- so i iterate through the center row seat, from a specific row say 'A' to 'F'. if after selecting every seat in the single row it didnt meet the desired ticket count(i want checking for available or unavailable seats. i was brute forcing my way through it.), we move to the next row
- if no center rows, then we iterate through the left side rows, and then the right side rows.
- we then book, and proceed to payment. that where the automation ends. 
- when we initate the payment, a push notification is sent to paytm with a timer of 15 minutes. if we didnt do the payment by then. then we payment request expires. 

- FYI, we did book our tickets with this bot.

## Selenium setup in Cloud  

```bash
apt update \
&& apt install -y wget unzip \
&& wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb \
&& apt-get install -y -f ./google-chrome-stable_current_amd64.deb \
&& wget https://storage.googleapis.com/chrome-for-testing-public/149.0.7827.155/linux64/chromedriver-linux64.zip \
&& unzip chromedriver-linux64.zip \
&&  mv  chromedriver-linux64/chromedriver /usr/local/bin/ \
&&  google-chrome --version \
&& chromedriver --version \ 
```
