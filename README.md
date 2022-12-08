# FOOTBALLSCOREBOARD
#include <iostream>
#include <string> 
#include <unistd.h>
#include "header.h"
#include <windows.h>
using namespace std; 

class Team 
{
  private:
    int score; 
    bool homeStatus; 
    string name;  
    string coachName;
int timeouts;
string city;
  public:
      Team() 
      {
        score = 0; 
        homeStatus = false; 
        name = "TEAMNAME"; 
      timeouts = 5;
        coachName = "coach"; 
      }
      void setScore(int s) { score = s; }
      void setHomeStatus(bool hs) { homeStatus = hs; }
void setCity(string c) {city = c; }
void setTimeout(int tO) {timeouts= tO;}
string getCity() const {return city;}
int getTimeout() const {return timeouts; }
      void setName(string n) { name = n; }
      void setCoachName(string sCN) { coachName = sCN; }
      int getScore() const { return score; }
      bool getHomeStatus() const { return homeStatus; }
      string getName() const { return name; }
      string getCoachName() const { return coachName; }
};

class Scoreboard
{
  private:
    int qtr; 
    Team home; 
    Team visitor; 

  public: 
    Scoreboard()
    {
      qtr = 1; 
    }  
    void setqtr(int q) { qtr = q; }
    void setHome(Team hSet) { home = hSet; }
    void setVisitor(Team vSet) { visitor = vSet; }
    int getqtr() const { return qtr; }
    Team getHome() const { return home; }
    Team getVisitor() const { return visitor; }

void showBoard()
{
 
  cout << "\tFootball ScoreBoard -- SAADSTYLE\n\n";
  cout <<home.getName() << "\t\t" << visitor.getName()<< endl;
  cout <<home.getScore() << "\t\t\t\t" << visitor.getScore() <<endl;
  cout << home.getTimeout() << "\t:TIMEOUTS:\t" << visitor.getTimeout()<< endl; 
  cout << home.getCoachName() << "\t\t " << visitor.getCoachName() << endl;
  cout << "QTR: " << getqtr() << endl;

        for(int i = 0; i < 40; i++) { cout << "-"; } cout << endl;

  cout << "Home Team> \t"; 
       if(home.getHomeStatus() == true)
       {
         cout << "Team 1: " << home.getName() << "*"; 
       }
       else if(visitor.getHomeStatus() == true)
       {
         cout << "Team 2: " << visitor.getName() << "*"; 
       }
       else
       {
         cout << "Error: "; 
       }
       
       cout  << endl; 
    }
};
int main()
{
  Scoreboard s;
  Team team1;
  Team team2;

  int timouts;
  string choice;
  int newscore;
  string newName;
  string newCoach;
int homeTeamQuestion = 0;
  int teamchoice = 0;
  
  
  team1.setHomeStatus(true);
s.setHome(team1); 
  s.setVisitor(team2); 


  do{
    system("clear");
    s.showBoard();

  
      cout << "A = Update Team Name" << endl; 
      cout << "B = Update Team Score" << endl; 
      cout << "C = Update Home Status" << endl; 
      cout << "D = Update  Team Coach" << endl; 
      cout << "E = Update Timeouts" << endl;
    cout << "F = Exit" << endl;
      cout << ">"; 
      cin >> choice; 

      if(choice == "A" || choice == "a")
      {
       
        cout << "****Update Team Name module*** " << endl; 
        cout << "which team would you like to make changes to(1-2): ";
        cin >> teamchoice;
        if (teamchoice == 1){
        cout << "\nPlease enter a new name for the home team: ";
        cin >> newName; 
        team1.setName(newName); 
          }
        else
        {
          cout << "\nPlease enter a new name for the visitor team: ";
        cin >> newName; 
        team2.setName(newName); 
          }
      }
      else if(choice == "B" || choice == "b")
      {
        cout << "\nUpdate  Score Module****" << endl; 
         cout << "which team would you like to make changes to(1-2): ";
        cin >> teamchoice;
        if (teamchoice == 1){
        cout << "\nPlease enter a new name for the home team: ";
        cin >> newscore; 
        team1.setScore(newscore); 
          }
        else
        {
          cout << "\nPlease enter a new name for the visitor team: ";
        cin >> newName; 
        team2.setScore(newscore); 
          }       
      }
      else if(choice == "C" || choice == "c")
      {
        cout << "\nUpdate Home Status Module****" << endl; 
        cout << "\nWho is the home team: 1 = TEAM1, 2=T2: "; 
        homeTeamQuestion = validateInt(homeTeamQuestion); 
       // cin >> homeTeamQuestion; 
        if(homeTeamQuestion == 1)
        {
          team1.setHomeStatus(true); 
          team2.setHomeStatus(false); 
        }
        else if(homeTeamQuestion == 2)
        {
          team1.setHomeStatus(false); 
          team2.setHomeStatus(true);
        }
        else
        {
          cout << "\nInvalid Input!" << endl;
          sleep(2); 
        }
      }
      else if(choice == "D" || choice == "d")
      {
          cout << "\nUpdate Visitor Coach Module****" << endl; 
           cout << "which team would you like to make changes to(1-2): ";
        cin >> teamchoice;
        if (teamchoice == 1){
        cout << "\nPlease enter a new coach for the home team: ";
        cin >> newCoach; 
        team1.setCoachName(newCoach); 
          }
        else
        {
          cout << "\nPlease enter a new coach for the visitor team: ";
        cin >> newName; 
        team2.setCoachName(newCoach); 
          }       
      }
      else if(choice == "E" || choice == "e")
      {
        cout << "Update Timeout Module****" << endl; 
          cout << "which team would you like to make changes to(1-2): ";
        cin >> timouts;
        if (teamchoice == 1){
        cout << "\nPlease enter a new timeout for the home team: ";
        cin >> timouts; 
        team1.setTimeout(timouts); 
          }
        else
        {
          cout << "\nPlease enter a new timeout for the visitor team: ";
        cin >> newName; 
        team2.setTimeout(timouts); 
          }       
      }
      else 
      {
        cout << "\nInvalid input." << endl; 
        sleep(2); 
      }

      s.setHome(team1); 
      s.setVisitor(team2); 
  s.showBoard();
  }while(choice != "F" && choice != "f");


  return 0; 
}
