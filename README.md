# Assignment Promises
This assignment consists of two separate exercises. Exercise 1 (Movie Search) is required and exercise 2 (Blackjack) is a stretch assignment.

For both exercise 1 and exercise 2 you will use the promise-based http fetch library called Axios.

You will primarily use `axios.get(url)` to interact with the APIs in the exercises. By following the documentation for each API, you will change the URLs that you pass to `axios.get(url)` to solve each exercise. The Blackjack exercise will require that you pass data from reponses into the url of a subsequent request.

To understand how a URL is constructed see this article titled ['What is a URL?'](https://developer.mozilla.org/en-US/docs/Learn/Common_questions/What_is_a_URL).

# Assignment Promises - Movie Search
The [OMDb API](https://www.omdbapi.com/) is a movie API that you can use to retrieve information about movies. To use this API, you will need to obtain a authentication key. To obtain the key go to [omdbapi.com](https://www.omdbapi.com/) and click on 'API Key' in the header toolbar. Select 'Free!' and then enter your email address. You will receive an email with your key and you will have to click an activation link to activate your key.

1. Obtain a key for the OMDb API following the instructions above.
1. `cd 1-movie-search`
1. Initialize the `1-movie-search` folder as an npm repository using `npm init`.
1. Install `axios` using `npm`.
1. Add a `.gitignore` file that contains `node_modules`.
1. Create an `omdb.js` file. (`omdb.js` will be a module that we will use to interact with the OMDb API in our main `index.js` file.)
1. Within `omdb.js` export a function called `search(term)` that takes a single search string as a parameter and returns the search results object.
1. Use the OMDb API, async/await, and axios to retrieve the search results of the term passed into the function. See the 'By Search' section of the OMDb documentation to see how to use the search API. Remember, axios places the returned data into a `data` property, so you will want to return the contents of that property. The search url will take the form of `http://www.omdbapi.com/?s=search_term&apikey=your_api_key`.
1. Create an `index.js` file.
1. Import your `omdb` module into `index.js`.
1. Create a `run` function that uses async/await.
1. Within the `run` function make a call to `omdb.search('lion')`
1. Log to the console the titles and release years of the first three movies returned and the total number of search results.
```
The Lion King 1994
The Chronicles of Narnia: The Lion, the Witch and the Wardrobe 2005
Lion 2016
Total Results: 508
```

# Stretch Assignment Promises - Deck of Cards
We will use the 'Deck of Cards' API to simulate the start of a game of blackjack with two players and one dealer.

The 'Deck of Cards' API provides an API to work with a virtual deck of cards. With this API we can create a deck of cards, draw cards from that deck, and place the drawn cards into piles. The documentation for this API is located at [deckofcardsapi.com](http://deckofcardsapi.com/).

At the start of a game of blackjack all of the players and the dealer have two cards. In our game of blackjack we will have one dealer, two players, and one deck of cards. We will first need to create a deck of cards. Next, we will then draw a card from the deck and deal it to the correct player (add it to the players pile). The correct order of dealing the cards is player1, player2, and the dealer until each player has two cards.

To solve this exercise, we will use the following URLs from the Deck of Cards API:
* 'A Brand New Deck' to create a new deck of cards with a unique `deck_id`. `https://deckofcardsapi.com/api/deck/new/`
* 'Draw a Card' to draw one or more cards from the deck based on the `deck_id`. `https://deckofcardsapi.com/api/deck/<<deck_id>>/draw/?count=<<draw count>>`
* 'Adding to Piles' to add the drawn cards to the pile of each player and the dealer. `https://deckofcardsapi.com/api/deck/<<deck_id>>/pile/<<pile_name>>/add/?cards=2S`
* 'Listing Cards in Piles' to list the pile of each player and dealer. `https://deckofcardsapi.com/api/deck/<<deck_id>>/pile/<<pile_name>>/list/`

1. `cd 2-blackjack`
1. Initialize the `2-blackjack` folder as an npm repository using `npm init`.
1. Install `axios` using `npm`.
1. Add a `.gitignore` file that contains `node_modules`.
1. It is your choice how you want to architect your application. However, you will need to follow the blackjack rules above to deal cards to each player in the correct order (player1, player2, dealer).
1. Validate that your piles are correct by console logging the pile associated with each player. An unshuffled deck should result in the following piles:
```
player1: AS,4S
player2: 2S,5S
dealer: 3S,6S
```
