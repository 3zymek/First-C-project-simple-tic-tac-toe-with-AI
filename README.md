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
