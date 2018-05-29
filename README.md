# Flashcards
Serve and order a flashcard stack based on how well you've memorized its content.  

The following is documentation for the free "smart" flashcard server available at: https://colarusso.github.io/flashcards/ "What's a 'smart' flashcard server?" you ask. Read on to find out. 

## Context

When I studied for the bar, I reduced my notes to not quite three thousand "flashcards." In truth, they were virtual flashcards. I created a database of 2,705 question-answer pairs and put them up on a web server. I accessed the server from my phone which presented the questions as cards based on how well the server thought I knew the material. 

I'd view a question (the front of a card), answer it, check the answer (the back of the card), and tell my phone whether I got it right or wrong. Based on this reporting, the server would figure out where to put the card in the metaphorical stack. If I always got a question right, the card went to the back of the queue. If I never got it right, it stayed near the front, and as the balance of my answers moved from wrong to right, a card's position drifted to the back. The cards were categorized based on the topics on the Bar and I could dive in based on a topic of my choosing or a representative mix of topics.

As a consequence, I always had my cards with me, and I always knew I was reviewing the material I needed to work on most. In fact, the ordering was based on the calculation of a confidence score which effectively was an estimate of how likely I was to "know" the content. So I actually had a pretty good sense of where I was. To be clear the most important part was probably the fact that the data entry forced me to distill and engage with my notes in a meaningful way. Whatever the case, I look back fondly on what I called the BarBot.

Since passing the bar, I haven't really had the need to commit such a large amount of information to memory. However, I recently started teaching full-time at Suffolk Law, and I wanted an easy way to memorize student names. Traditionally, I make flashcards with student photos so I can greet students on the first day by name. It occurred to me that it would be pretty cool if I could do my review on the train during my commute. So I decided to revisit the virtual flashcard idea. Inspired by one of my [student's projects](https://github.com/SuffolkLITLab/resource-map-how-to), I decided to run the whole thing off GitHub Pages and Airtable. Consequently, anyone can create their own set of cards by making an Airtable (free on-line spreadsheet) and access it by following the directions below. 

## How To

0. Create an [Airtable](https://airtable.com/) account if you don't already have one.
1. Create an Airtable with the columns: "front", "back", "up", "down", "score", and "last," where "up", "down", "score", and "last" are number columns. You can use [this base](https://airtable.com/invite/l?inviteId=inveUUpZ4jP9hE66M&inviteToken=51b69eab0d648b22ff6dc9507089b0572664d33cfb197d14f84e1d0e00034d98) as a template if you like. Just click on the title then "Duplicate Base." You can then add your own tables.

![Duplicate](https://colarusso.github.io/flashcards/images/duplicate.gif)

2. Fill your Airtable with your cards by placing your desired text or the URL of an image in both the "front" and "back" cells of a row. The other columns will capture the history of your interactions (e.g., how many times you got it right). 
3. Note your API key (instructions below), the table's base ID (instructions below), and the table's name (instructions below). 
4. Visit https://colarusso.github.io/flashcards/, enter the info from 3 into the prompts, and have at it. 

### Your API Key

To find your API key, after logging in, visit your [account page](https://airtable.com/account). It will be listed under *API Key*.

### Your base ID

To find your bases' ID, click on the *Help* link then *API Documentation*. This will open a new window. The string of text between `https://airtable.com/` and `/api/docs#curl/introduction` is your Base ID. 

![Base ID 1](https://colarusso.github.io/flashcards/images/base.gif)

![Base ID 2](https://colarusso.github.io/flashcards/images/baseid.png)

### Your table name

Your table name is the name of the tab your table displays in. For example, "flags."

![Table Name](https://colarusso.github.io/flashcards/images/flags.png)

*Note: [SeRiouS](https://www.spacedrepetition.com/) offers a virtual flashcard system for bar prep similar to the one described here. It didn't exist back when I took the bar, but if you don't want to create a few thousand cards from scratch, they have a nice set of decks made by professionals. Also, the company's run by a good friend of mine. FWIW, I do **not** have a financial stake in the company. I just find it interesting.*
