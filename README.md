# Turn Spreadsheets into Flashcards
Serve and order a stack of virtual flashcards based on how well you've memorized its content: (1) make a spreadsheet with columns for the "front" and "back" of your cards; (2) add your content as rows to the sheet; (2) link that sheet to the [web app](https://colarusso.github.io/flashcards/); and (3) work your way through the cards. Context and instructions below.

![example](https://colarusso.github.io/flashcards/images/flips.gif)

## Context / Backstory

When I studied for the bar, I reduced my notes to not quite three thousand "flashcards." In truth, they were virtual flashcards. I created a database of 2,705 question-answer pairs and put them up on a web server. I accessed the server from my phone which presented the questions as cards based on how well the server thought I knew the material.

I'd view a question (the front of a card), answer it, check the answer (the back of the card), and tell my phone whether I got it right or wrong. Based on this reporting, the server would figure out where to put the card in the metaphorical stack. If I always got a question right, the card went to the back of the queue. If I never got it right, it stayed near the front, and as the balance of my answers moved from wrong to right, a card's position drifted to the back. The cards were categorized based on the topics on the Bar and I could dive in based on a topic of my choosing or a representative mix of topics.

As a consequence, I always had my cards with me, and I always knew I was reviewing the material I needed to work on most. In fact, the ordering was based on the calculation of a confidence score which effectively was an estimate of how likely I was to "know" the content. So I actually had a pretty good sense of where I was. To be clear the most important part was probably the fact that the data entry forced me to distill and engage with my notes in a meaningful way. Whatever the case, I look back fondly on what I called the BarBot.

Since passing the bar, I haven't really had the need to commit such a large amount of information to memory. However, I recently started teaching full-time at Suffolk Law, and I wanted an easy way to memorize student names. Traditionally, I make flashcards with student photos so I can greet students on the first day by name. It occurred to me that it would be pretty cool if I could do my review on the train during my commute. So I decided to revisit the virtual flashcard idea. Inspired by one of my [student's projects](https://github.com/SuffolkLITLab/resource-map-how-to), I decided to run the whole thing off GitHub Pages and Airtable. Consequently, anyone can create their own set of cards by making an Airtable (free on-line spreadsheet) and access it by following the directions below.

## How To

You can use Airtable as described below, or select **Local CSV** in Settings and upload **multiple CSV files** with `front` and `back` columns. The saved CSV files and compatible Airtable tables appear as radio options above **Cooling Off**, each showing its card count. Choose the deck you want, then click **Save & Start**. In Local CSV mode, **Delete CSV** removes the selected file and its saved review history from this browser; **Export CSV** and **Reset Counts** apply only to the selected deck. Older single-CSV browser data is migrated automatically.

**Cooling Off** controls the minimum number of *other questions* that must be shown before a card can return. For example, with Cooling Off set to `2`, answering A means neither the next question nor the one after that can be A; A becomes eligible on the third subsequent question. Set it to `0` to allow immediate repeats. This is enforced per card, not by an elapsed time or a shared counter. It must be smaller than the selected deck’s card count. Each card’s `last` review value stores its position in the recent review order so the exclusion survives restarting the app (for CSV/local progress in this browser and for full-progress Airtable tables via their saved `last` field).

0. Create an [Airtable](https://airtable.com/) account if you don't already have one.
1. Create one or more Airtable tables with at least **front** and **back** fields. For scores and review history to sync back to Airtable, add **up**, **down**, **score**, **last**, and **random** fields (the first four are number fields). Tables that only have **front** and **back**, or lack some progress fields, can still be reviewed: their progress is stored in your browser instead. You can use [this base](https://airtable.com/invite/l?inviteId=inveUUpZ4jP9hE66M&inviteToken=51b69eab0d648b22ff6dc9507089b0572664d33cfb197d14f84e1d0e00034d98) as a template if you like. Just click on the title then "Duplicate Base." You can then add your own tables.

![Duplicate](https://colarusso.github.io/flashcards/images/duplicate.gif)

2. Fill your Airtable with your cards by placing your desired text or the URL of an image in both the "front" and "back" cells of a row. The other columns will capture the history of your interactions (e.g., how many times you got it right).
3. Create an Airtable [personal access token](https://airtable.com/create/tokens) with **schema.bases:read** and **data.records:read** scopes, plus **data.records:write** if using the progress columns. Give it access to the base you intend to use. Find that base's ID ([instructions](#your-base-id) below).
4. Open the app, select **Airtable**, and enter only the **token** and **Base ID**. The app automatically lists tables that have `front` and `back` fields and counts their records (including tables with more than 100 cards). Choose a table and click **Save & Start**. Use **Refresh Airtable Tables** to rescan after creating or modifying tables.

### Saving the app

When you bookmark the app or add it to your phone's home screen, its default name is **Flashcards** no matter whether Settings, About, or a card is currently showing. The on-screen page headings still identify the active screen. The **About** page also explains `(card% | deck%)` and how the selected decks are managed.

### Pro Tips

* If you are using a keyboard, press Space to flip a card, ↑ for <i>Knew It</i>, or ↓ for <i>Didn't Know It</i>.
* You can clear out the history of your interactions by editing your table directly (e.g., deleting all the entries other than *front* and *back*).
* The two percentages in the parenthetical at the top of a card are `(card% | deck%)`. The first is the system's prediction that you will get the current card right; it starts at 50% and moves up or down based on your interactions. The system moves cards with the lowest score to the top of your stack. This score is an approximation of the [Wilson Confidence Interval](https://en.wikipedia.org/wiki/Binomial_proportion_confidence_interval#Wilson_score_interval). The second percentage is the average score across **all** cards in the current deck (sum of the cards' scores divided by the number of cards, rounded to a whole percent). It is a measure of overall readiness, not the mathematical probability of getting every card right in one attempt.
* If you place the url for an image (`.jpg`, `.gif`, or `.png`) in either the "front" or "back" column of your sheet, the web app will display the image (e.g., the picture of a state flag from wikipedia).
* You can add multiple tables to a single base and select between them in the web app; a selected table's review scores are kept separate.  
* You aren't restricted to plain text. You can use html to when wrting your cards.

*Note: [SeRiouS](https://www.spacedrepetition.com/) offers a virtual flashcard system for bar prep similar to the one described above. It didn't exist back when I took the bar, but if you don't want to create a few thousand cards from scratch, they have a nice set of decks made by professionals. Also, the company's run by a good friend of mine. FWIW, I do **not** have a financial stake in the company. I just find it interesting. That being said, I'm sure not everyone reading this is studying for the bar.*

### Your Airtable token

Airtable's old API keys have been retired. Use a [personal access token](https://airtable.com/create/tokens) with `schema.bases:read` to discover table schemas and `data.records:read` to count and review cards. Add `data.records:write` to save progress directly to Airtable when the five progress fields are present. Only grant access to the bases you want to review.

### Your base ID

To find your bases' ID, click on the *Help* link then *API Documentation*. This will open a new window.

![Base ID 1](https://colarusso.github.io/flashcards/images/base.gif)

The string of text between `https://airtable.com/` and `/api/docs#curl/introduction` is your Base ID. It should look something like this `appH6ratSHISfBjvC`.

![Base ID 2](https://colarusso.github.io/flashcards/images/baseid.png)

### Choosing a table

There is no table-name field to fill in: compatible tables are listed automatically, with their number of cards. Select a radio option to choose the deck. The list refreshes when you change credentials or press **Refresh Airtable Tables**.

### Loading a CSV from a link

You can share a link that imports a CSV into the **Local CSV** list. Append `?load=` and the URL of a `.csv` file to the flashcard app URL, for example:

```text
https://example.com/flashcards/?load=https%3A%2F%2Fexample.org%2Fcards%2Fgeography.csv
```

The app downloads the CSV, checks for `front` and `back` columns, and adds it to the saved CSV decks **with its filename and card count**. The imported deck is selected automatically; click **Save & Start** to begin studying. Existing CSV decks remain untouched. Revisiting the **same URL** selects the previously imported copy (including its review progress) rather than creating a duplicate. Delete that copy first if you need to re-import revised contents from the same URL.

**Requirements:** The link must point to an HTTP(S) URL whose path ends in `.csv` (case insensitive; CSV URLs may include query parameters). The server hosting the CSV must permit cross-origin browser requests through **CORS** unless the file is served from the flashcards app's own origin. A normal file download link that blocks CORS, requires login, or redirects to HTML will not work. Failed imports show an error in Settings. Encode the CSV URL with `encodeURIComponent` so any `?` or `&` within the CSV URL is handled correctly. For example:

```javascript
const shareLink = 'https://example.com/flashcards/?load=' + encodeURIComponent('https://example.org/cards/geography.csv?version=2');
```

### Multiple CSV storage

Local CSV decks and their review progress are stored in your browser’s `localStorage`, not uploaded to a server. Uploading files adds them to the list (it does not overwrite existing files), even if the filenames match. Large decks may reach the browser’s storage quota. Delete CSV permanently removes just the selected local file. Tables without Airtable progress fields use per-base, per-table browser storage for scoring; on another device, those scores will not follow you.
