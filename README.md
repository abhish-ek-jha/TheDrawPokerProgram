# TheDrawPokerProgram
/*This C program plays draw poker.Users can play as often as they want,betting between 1 and 5.They are dealt 5 cards and then got to choose
cards which cards to keep and which card to replace.The new hand is then reviewed and the user's payout is set based on the value of the hand.
The user's new bankroll is displayed as they are given the option to continue */

//Header files

#include<stdio.h>
#include<time.h>
#include<ctype.h>
#include<stdlib.h>

//Two constants defined for determining whether hands are flushes or straights

#define FALSE 0
#define TRUE 1

//Function Prototyping

void printGreeting();
int getBet();
char getSuit(int suit);
char getRank(int rank);
void getFirstHand(int cardRank[], int cardSuit[]);
void getFinalHand(int cardRank[], int cardSuit[], int finalRank[], int finalSuit[], int ranksinHand[], int suitsinHand[]);
int analyzeHand(int ranksinHand[], int suitsinHand[]);

int main()
{
  int bet;
  int bank=100;
  int i;
  int cardRank[5];   //Will be one of 13 values(Ace-King)
  int cardSuit[5];   //Will be one of 4 values(for clubs, diamonds, hearts,spades)
  int finalRank[5];
  int finalSuit[5];
  int ranksinHand[13];  //Used for evaluating the final hand
  int suitsinHand[4];   //Used for evaluating the final hand
  int winnings;
  time_t t;
  char suit, rank, stillPlay;
  
  //This function is called outside the do...while loop because the greeting
  //only need to be displayed once, while everything in main will run multiple times,
  //depending on how many times user wants to play
  
  printGreeting();
  
  
  //loop runs each time the user plays a hand of draw poker
  
  do{
      bet = getBet();
      srand(time(&t));
      getFirstHand(cardRank, cardSuit);
      printf("Your five cards:  \n");
      for(i=0; i<5; i++)
      {  
          
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
