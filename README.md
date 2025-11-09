Code Structure
The game is organized into 4 main parts:

1. Card & Deck Classes
These handle the basic playing cards:

Card - Represents a single card with a rank (2-A) and suit (Hearts, Diamonds, etc.)
Deck - Creates a full 52-card deck, shuffles it, and deals cards. When cards run low, it automatically creates and shuffles a fresh deck
2. Hand Class - The Brain of the Game
This is where the magic happens! When you get 3 cards, this class:

Sorts your cards by value (highest first)
Evaluates your hand by checking for patterns:
Counts how many of each card value you have (for pairs and three of a kind)
Checks if all suits match (for flushes)
Checks if values are in sequence (for straights)
Combines both checks (for straight flushes)
Assigns a rank so hands can be compared (higher rank wins)
The comparison happens automatically - when the game checks if player_hand > dealer_hand, Python uses the ranking system to determine the winner.

3. ThreeCardPoker Class - The Game Manager
This runs the entire game and handles:

Money tracking:

Starts you with $1,000
Deducts bets when you place them
Adds back winnings based on the outcome
Game flow:

Shows you the rules
Asks for your bet
Deals cards to you and the dealer
Gets your Play or Fold decision
Reveals the dealer's hand
Calculates and displays the results
4. The Payout System - Following Casino Rules
This was the trickiest part! Here's how payouts work:

When you fold:

You lose your Ante bet (already taken out)
Nothing gets added back
When you play:

First, check for Ante Bonus - If you have a Straight or better, you get bonus money REGARDLESS of whether you win or lose
Then, determine the outcome:
Dealer doesn't qualify? You get your Ante back + winnings, plus your Play bet is returned
You win? Both bets come back + equal winnings (you double your money)
Tie? Both bets are returned (break even)
Dealer wins? Bets are lost, but you still keep any Ante Bonus
The key trick: bets are removed from your balance immediately when placed, so the payout calculation just figures out what to add back to your balance.

How a Round Works
You place an Ante bet → money comes out of your balance
Cards are dealt to both you and the dealer
You decide to Play (bet again) or Fold
If you Play → another bet comes out
Game calculates what you've won → adds it back to your balance
Shows you the net result (what you gained or lost overall)
That's it! The game loops until you run out of money or decide to quit. Everything follows standard casino 3 Card Poker rules.
