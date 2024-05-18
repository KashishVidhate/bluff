# Bluff ... ♠️♥️♦️♣️
A run-in-terminal game of Bluff, I wrote this game as a course project for my subject "Problem solving and Programming in C"
It's been more than a year today and when I look back to this code im terrified !  It's neither optimized nor follow any proper structure,
because I was new to programming and I remember clearly I made this after a month I had a idea in one "night",I just fear if I touch it, I'll break it
my friend Soham helped me.

Heyy...But it works ! 🙂

The project was supposed to use any data structure, the game implements STACK data structure.
Once my friend was explaning me this game, and i noticed that the putting of cards on table and picking them up was 
very simliar to a STACK ... so i made it.

# How to play ?
Just open the "bluff-game.c" file in any IDE (VSCode preferred), and hit "RUN" button, and then open the terminal fully {easier to play} wait a sec,
and then just follow the instructions on the screen, and Enjoy ! 
## Aim
The aim of the game is to loose all the cards as soon as possible without being caught bluffing.
In game only number of cards and their rank matter, Ace, Joker, Queen and King have rank as 1, 11, 12 and 13 respectively


## Default settings
By default game starts with 1 deck of cards and 5 players, You can change the following macros in code if you want to and restart the game
```
#define no_of_players 5
#define no_of_deck 1
```
I guess names are pretty self explanatory.

# Steps
When you strat the game, the welcome screen would look something like as following

```
                                ~~~~~ THE ART OF BLUFFING ~~~~~

                                        1. START GAME.
                                        2. EXIT.

                DEFAULT:
                DECK : 1
                PLAYERS: 5

                         Option <<
```
The number to the left of an action is to be pressed to take that action
You option choice would appear after:
```
Option <<
```

### Option 1
Press '1' and hit enter to actually start playing.

### Option 2
Press '2' and hit enter to exit.

## After pressing '1'
The new text on screen may looks something as following:

```

                                ~~ PLAYER 1 ~~

                1. SHOW cards.
                2. SHOW and CALL.
                3. SHOW and PASS.
                4. BLUFF !.
                5. KILL game.

                         Last CALL, 0 cards of 0 rank each.


                         Option <<

```
This is player dashboard, each player would be displayed this screen at there turn.

```
 ~~ PLAYER 1 ~~
```
This tells which players turn is currently ongoing.

```
1. SHOW cards.
```
This option ***only*** shows your cards, this option ***does not*** end your chance 

### After pressing `1`

A warning message would appear, you and your friends are supposed to play on same laptop, so thats why the warning.
```

                         ~~~~~~~~ ! MAKE SURE NOBODY ELSE IS WATCHING ! ~~~~~~~~

                                Press Enter if all clear, and continue
```
Press enter.
The dashboard would be updated as follwing, showing you your cards
```
                                ~~ PLAYER 1 ~~

                1. SHOW cards.
                2. SHOW and CALL.
                3. SHOW and PASS.
                4. BLUFF !.
                5. KILL game.

                         Last CALL, 0 cards of 0 rank each.


                        Your cards << 2 4 4 6 6 6 9 11 12 13

                         Option <<
```
The cards are arranged in ascending order, so its easier to see how many similar cards you have.

```
2. SHOW and CALL.
```
This option would ***show*** you your cards and ***make*** the call, this option ***will*** end your chance.


### After pressing '2'
The promt you get is
```
                How many cards, you want to keep on Table ? :
```
In real life game you call 2 number while putting the cards on table, 
e.g. (2 6) , this means you are *honestly* putting 2 cards of rank 6.
, e.g. (1 13), this means you are *honestly* putting 1 king on the table.
and so forth...

Enter single intger number and press enter 

(the might broke if some other input is given, I have not handeled all edge cases)

I entered `3` in the following example, the new prompt is as follows:

```
                How many cards, you want to keep on Table ? : 3

                What is the Rank of each card ? (other's can see this) :
```

Now here you have to press each integer seperated by space representing each card in the call
(You may or may not be honest), but you have to put exactly '3' cards as you called, guessing if you bluffed or not is next players headache

***BE CAREFUL WHILE ENTERING THE NUMBERS***

I entered `6 6 6` as the input, cause I had three 6 cards, make sure not to give __extra__ space after last input,
The new prompt is a warning message, because after that you have to be honest so that computer would know the real cards
you 'put' on table.

```

                How many cards, you want to keep on Table ? : 3

                What is the Rank of each card ? (other's can see this) : 6 6 6

                                 ~~ MAKE SURE NOBODY IS WATCHING ~~

                          Press Enter to continue: 

                 Actuall Ranks of the cards you kept (other's can't see this):
```

Now enter the actual integers, seperated by space corresponding to actual cards you kept on the table (dont lie to computer, or the game logic goes down)

If you were honest then this sequence will be same as previous sequence.
If you were bluffing then this sequnce will be different from the previous sequence.
But in both the cases the count of the cards should be same.

```

                How many cards, you want to keep on Table ? : 3

                What is the Rank of each card ? (other's can see this) : 6 6 6

                                 ~~ MAKE SURE NOBODY IS WATCHING ~~

                          Press Enter to continue: 

                 Actuall Ranks of the cards you kept (other's can't see this): 6 6 6

                        Your cards NOW <<  2 4 4 0 0 0 9 11 12 13 

                          Press Enter to finish your turn.
```
In above example I choose to be honest.

The cards you enter while telling the computer will be removed from your cards list and will be replaced by `0`
(this are the cards you actually kept). Press enter to finish your turn.

### After pressing `3`

If you pressed the option `3` :

```
3. SHOW and PASS.
```
This option will ***only*** show you your cards and ***will end*** your chance.
(pro tip: don't waste your chance)

# Next players Turn

After finishing the player 1's turn its player 2's turn, the similar dashboard appears

```

                                ~~ PLAYER 2 ~~

                1. SHOW cards.
                2. SHOW and CALL.
                3. SHOW and PASS.
                4. BLUFF !.
                5. KILL game.

                         Last CALL, 3 cards of 6 rank each.


                         Option <<
```

The new information on this dashboard is __last call__, every new player will be able to see the last call made by previous player
(if made), or the most recent call.

```
Last CALL, 3 cards of 6 rank each.
```
based on this call you have to choose if previous player was honest or not, the call says
> the previous player ***honestly*** kept 3 cards of 6 rank each.

You can either choose option `2` or `3` or `4` in this situation (according real life)

### If you choose option `2`

It means you guess that player was ***HONEST*** and you choose to put your cards on top of the stack and end your turn.

### If you choose option `3`

It means you player was ***HONEST*** and you choose not to increase the stack on the table and end yourn turn.

### If you choose opyion `4`

This one is interesting, This means you guess that player was indeed ***BLUFFING*** and choose to pick the cards from the table.
Now ony 2 thins can happen in this scenario.

### Player was Honest

If the plaer was honest, all the cards on the table will be added to your sequence of the cards, and your turn would end.

### Player was Buffing

If player was bluffing, all the cards on the table will be added to previous players sequence of the cards, and your turn would end

If you choose this option new promt would appear,

```

                                  Player 2 called BLUFF on PLayer 1

                 PLayer 1 called 3 cards of 6 rank each, but actually kept this cards: 6 6 6


                         ~~~~~~~ PLAYER 1 was HONEST ! ~~~~~~~


                          ~~~~~~~ PLAYER 2 GUESSED WRONG ! ~~~~~~~


                                 Press Enter to continue
```
The first line tells about the recent move,
The second line revels the actual cards on the table.
The third line declares the honesty of the player under charge.
The fourth line declares if the current player was right or wrong.

Press enter to continue.

***... CONTINUE THE GAME***

## Pressing option `5`

```
5. KILL game.
```
This option will force end the game, before the winner is declared.
But first will promt this warning.

```
                 ~~~~~ GAME KILL WARNING ~~~~~

                 ~~~ YOU ( Player 3 ) are KILLING game ! ~~~~~


                 Enter 1 , if all Players agree to kill the game.

                 Enter 0 , to continue the game.

                                 Option <<
```

If option `1` is pressed, the following info page would be shown and game will stop.

```
                        ~~~~~ Thank you for your time ! ~~~~~


Developed @ Vishwakarma institute of Technology as DSA course project by >>

         Kashish V
         Shaunak K
         Kartik P
         Limay K
         Nikhil K

                 Press Enter to exit.
```


# Enjoy

Play , Enjoy and I encourage you to find as many bugs as posssible. 

