# First-C-project-simple-tic-tac-toe-with-AI
This is my first project in C++ (and on github also) to check my skills in it, and I am uploading it here as a future reference to track my progress.
🛠 Written in C++, compiled with g++  
🎯 Command-line based  
🧠 Random AI (for now!)
I uploaded this as a portfolio piece and memory for the future.

#include <iostream>
#include <cstdlib>
#include <string>
using namespace std;
char game[3][3];
int x,y,a,b;
int rounds=0;
bool player;
bool WinCheck()
{
    if(rounds>=9)
    {
        cout<<"End of the game, nobody wins."<<endl;
    }
    if(game[0][0]=='X'&&game[0][1]=='X'&&game[0][2]=='X')
        return true;
    else if(game[0][0]=='O'&&game[0][1]=='O'&&game[0][2]=='O')
        return true;
    else if(game[1][0]=='X'&&game[1][1]=='X'&&game[1][2]=='X')
        return true;
    else if(game[1][0]=='O'&&game[1][1]=='O'&&game[1][2]=='O')
        return true;
    else if(game[2][0]=='X'&&game[2][1]=='X'&&game[2][2]=='X')
        return true;
    else if(game[2][0]=='O'&&game[2][1]=='O'&&game[2][2]=='O')
        return true;
    else if(game[0][0]=='X'&&game[1][1]=='X'&&game[2][2]=='X')
        return true;
    else if(game[0][2]=='X'&&game[1][1]=='X'&&game[2][0]=='X')
        return true;
    else if(game[0][0]=='O'&&game[1][1]=='O'&&game[2][2]=='O')
        return true;
    else if(game[0][2]=='O'&&game[1][1]=='O'&&game[2][0]=='O')
        return true;
    else if(game[0][0]=='O'&&game[1][0]=='O'&&game[2][0]=='O')
        return true;
    else if(game[0][1]=='O'&&game[1][1]=='O'&&game[2][1]=='O')
        return true;
    else if(game[0][2]=='O'&&game[1][2]=='O'&&game[2][2]=='O')
        return true;
    else if(game[0][0]=='X'&&game[1][0]=='X'&&game[2][0]=='X')
        return true;
    else if(game[0][1]=='X'&&game[1][1]=='X'&&game[2][1]=='X')
        return true;
    else if(game[0][2]=='X'&&game[1][2]=='X'&&game[2][2]=='X')
        return true;
    else return false;
}
bool CheckInt()
{
    if(cin.fail())
    {
        cin.clear();
        cin.ignore(1000,'\n');
        cout<<"This is not a number."<<endl;
        return false;
    }
    return true;
}
void PlayerTurn()
{
    do
    {
    do{
    cout<<"Enter row and column (0-2): ";
    cin>>x>>y;}
    while(!CheckInt());
    if (game[x][y]=='-')
    {
        game[x][y]='X';
        player=true;
        rounds++;
    }
    else {
    cout<<"That spot is already taken."<<endl;
    player=false;
    }
    } while (!player);
}
void AITurn()
{
    do
    {
    a=rand()%(2+1);
    b=rand()%(2+1);
    } while (game[a][b]!='-');
    game[a][b]='O';
    rounds++;
    cout<<"AI round: "<<endl;
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            cout<<game[i][j];
        }
        cout<<endl;
    }
}
void ShowTab()
{
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            cout<<game[i][j]<<" ";
        }
        cout<<endl;
    }
}
int main() {
    srand(time(NULL));
    cout<<"===================TIC TAC TOE FIRST PROJECT C++==================="<<endl;
    cout<<"                         YOU PLAY AS 'X'"<<endl;
    for(int i=0;i<3;i++)
    {
        for(int j=0;j<3;j++)
        {
            game[i][j]='-';
            cout<<game[i][j]<<" ";
        }
        cout<<endl;
    }
    do{
    PlayerTurn();
    WinCheck();
    ShowTab();
    AITurn();
    WinCheck();
    if(WinCheck()){
        ShowTab();
        break;
    }
    }while(!WinCheck());
    cout<<"The end!"<<endl;
    system("pause");
}
