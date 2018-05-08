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
          suit = getSuit(cardSuit[i]);
          rank = getRank(cardRank[i]);
          printf("Card #%d: %c%c \n", i+1, rank, suit);
       }
       
       //These two arrays are used to figure out the value of the player's hand.
       //However, they must be zeroed out in case the user plays multiple hands.
       
       for(i=0; i<4; i++)
       {
            suitsinHand[i] = 0;
       }
       
       for(i-0; i<13; i++)
       {
          ranksinHand[i]=0;
       }
       
       getFinalHand(cardRank, cardSuit, finalRank, finalSuit, ranksinHand, suitsinHand);
       
      printf("Your five final cards:  \n");
      for(i=0; i<5; i++)
      {
        suit=getSuit(finalSuit[i]);
        rank=getRank(finalRank[i]);
        printf("Card #%d: %c%c  \n",i+1, rank, suit);
      }
      
      winnings= analyzeHand(ranksinHand,suitsinHand);
      printf("You won %d! \n",bet*winnings);
      bank=bank-bet+(bet*winnings);
      printf("\n Your bakn is now %d.\n",bank);
      printf(" \n Do you want to play again?");
      scanf("%c", &stillplay);
    }while(toupper(stillplay) == 'Y');
    
    return;
    
    }
      
   //print a quick greeting as well as tell the users the value of different winnings hands
   
   void printGreeting()
   {
      printf(" \t Home of Video Draw Poker Program \n \n");
      printf("Here are the rules:  \n");
      printf("You start with 100 credits, and you make a bet from 1 to 5 credits.  \n ");
      printf("You are dealt 5 cards and then you chooe which cards to keep or discard. You want to make the best possible hand.  \n");
      printf(" \n Here is the table for winnings(assuming a bet of 1 credit):");
      printf("\nPair\t\t\t1 credit");
      printf("\nTwo Pairs\t\t\t2 credits");
      printf("\nThree of a kind \t\t\t3 credits");
      printf("\nStraight\t\t\t4 credits");
      printf("\nFlush\t\t\t5 credits");
      printf("\nFull House\t\t\t8 credits"); 
      printf("\nFour of a kind\t\t\t10 credits");
      printf("\nStraight flush\t\t\t20 credits");
      printf("\n\n Have Fun!! \n\n");
   }
   
   //Function to deal the first five cards
   
   void getFirstHand(int cardRank[], int cardSuit[])
   {
    int i,j;
    int cardDup;
    
    for(i=0;i<5;i++)
    {
        cardDup = 0;
   do{
        //Card rank is one of 13(2-10, J, Q, K, A)
        cardRank[i]= (rand() % 13);
        //Card suit is one of 4 (club, diamond, spade, heart)
        cardSuit[i]= (rand() %4);
        
        //loop that ensures that each card is unique 
        for(j=0;j<i;j++)
        {
         if((cardRank[i]== cardRank[j]) && (cardSuit[i] == cardSuit[j]))
         {
            cardDup = 1;
         }
         }
         } while(cardDup == 1);
         }
         }
         
  //function that changes the suit integer value to a character representing the suit
  
  char getSuit(int suit)
  { 
      switch(suit)
      {
      
      case 0: return('c');
      case 1: return('d');
      case 2: return('h');
      case 3: return('s');
      
      }
      }
  
  //function that changes the rank integer value to a character representing the rank
  
  char getRank(int rank)
  {
    
  
  
  
  
  
  
  
  
  
  
  
