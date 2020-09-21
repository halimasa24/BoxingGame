# BoxingGame
/*
Name: Halima Afrah
Date: Spring 2020
Course: CSCI 1300: Starting Computing
Assignment: Project 3: Boxing Championship
*/


// Header implementings
#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>
#include <fstream>
#include "Opponent.h"
#include "Me.h"
using namespace std;


// Initialize
Me User;
Opponent Comp;
int stamina = 200;
int damage = 25;
int money;	
	bool G1D = false;
	bool G2D = false;
	bool G3D = false;
	bool P1H = false;
	bool P2H = false;
	bool P3H = false; 
	bool P4H = false;
void shop()
{

	int option;
	int Gloves1D = 25;
	int Gloves2D = 50;
	int Gloves3D = 75;
	int Pot1H = 25;
	int Pot2H = 50;
	int Pot3H = 75;
	int Pot4H = 100;
	int Money = 500;
	int Gloves1P = 250;
	int Gloves2P = 400;
	int Gloves3P = 500;
	int Pot1P = 100;
	int Pot2P = 250;
	int Pot3P = 400;
	int Pot4P = 500;

	money = 500;
	do
	{
		std::cout << endl;
		std::cout << endl;
		std::cout << "SHOP:" << endl;
		std::cout << "Item                       Increase                 Price" << endl;
		std::cout << "======================================================== " << endl;
		std::cout << "1: Purchase Gloves 1D:  25 Extra Damage:            $250 " << endl;
		std::cout << "2: Purchase Gloves 2D:  50 Extra Damage:            $400 " << endl;
		std::cout << "3: Purchase Gloves 3D:  75 Extra Damage:            $500 " << endl;
		std::cout << "4: Purchase Potion 1H:  25 Extra Stamina:           $100 " << endl;
		std::cout << "5: Purchase Potion 2H:  50 Extra Stamina:           $250 " << endl;
		std::cout << "6: Purchase Potion 3H:  75 Extra Stamina:           $400 " << endl;
		std::cout << "7: Purchase Potion 4H: 100 Extra Stamina:           $500 " << endl;
		std::cout << "8: Remaining Funds" << endl;
		std::cout << endl;
		cin >> option;

		switch (option)
		{
		case 1:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Gloves 1D For $250 " << endl;
			Money -= Gloves1P;
			damage += Gloves1D;
			std::cout << "Your Damage Is Now: " << damage << endl;
			User.setDamage(damage);
			G1D = true;
			break;
		case 2:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Gloves 2D For $400 " << endl;
			Money -= Gloves2P;
			damage += Gloves2D;
			std::cout << "Your Damage Is Now: " << damage << endl;
			User.setDamage(damage);
			G2D = true;
			break;
		case 3:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Gloves 3D For $500 " << endl;
			Money -= Gloves3P;
			damage += Gloves3D;
			std::cout << "Your Damage Is Now: " << damage << endl;
			User.setDamage(damage);
			G3D = true;
			break;
		case 4:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Potion 1H For $100 " << endl;
			Money -= Pot1P;
			stamina+= Pot1H;
			std::cout << "Your Stamina Is Now: " << stamina << endl;
			User.setStamina(stamina);
			P1H = true;
			break;
		case 5:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Potion 2H For $250 " << endl;
			Money -= Pot2P;
			stamina += Pot2H;
			std::cout << "Your Stamina Is Now: " << stamina << endl;
			User.setStamina(stamina);
			P2H = true;
			break;
		case 6:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Potion 3H For $400 " << endl;
			Money -= Pot3P;
			stamina += Pot3H;
			std::cout << "Your Stamina Is Now: " << stamina << endl;
			User.setStamina(stamina);
			P3H = true;
			break;
		case 7:
			std::cout << endl;
			std::cout << "Congratulations! You Have Purchased Potion 4H For $500 " << endl;
			Money -= Pot4P;
			stamina += Pot4H;
			std::cout << "Your Stamina Is Now: " << stamina << endl;
			User.setStamina(stamina);
			P4H = true;
			break;
		case 8:
			std::cout << endl;
			std::cout << "You Current Have: $" << Money << endl;
			break;
		default:
			std::cout << endl;
			std::cout << "Error 80310: Incorrect Value, Please Try Again!" << endl;
			break;
		}
	} while ( Money > 0 || option == 9);

}
int main()
{
	// Declare Variables
	string FirstName, playerName, line;
	string nameArray[10];
	string BoxerInformation[5];
	int ABC = 0;
	int CBA = 0;
	int choice = 0;
	int roundWins = 0;
	int weight = 0;
	int champNum = 0;

	// Functions
	/*
	void rules();
	*/


	// Open File and Pick Random Name
	srand((unsigned int)time(0));
	

	ifstream myFile;
	myFile.open("OpponentNames.txt");
	if (myFile.is_open())
	{
		while (!myFile.eof())
		{
			getline(myFile, nameArray[ABC], '\n');
			ABC++;
		}
	}
	// Initialize
	Me User;
	Opponent Comp;



	// Return Information From Classes
	//UserStamina = User.getStamina();
	//CompStamina = Comp.getStamina();



	bool Win = false;
	std::cout << "Welcome To USBC (United States Boxing Championship!" << endl;
	std::cout << "Please Register First, Then Select Desired Next Option: " << endl;
	ofstream BoxerFile;
	BoxerFile.open("BoxerInfo.txt", ios::out | ios::in);
	do
	{
		std::cout << endl;
		std::cout << "======================================================= " << endl;
		std::cout << "1: Register Fighter" << endl;
		std::cout << "2: Fighting Instructions/Rules" << endl;
		std::cout << "3: Shop" << endl;
		std::cout << "4: Inventory" << endl;
		std::cout << "5: Enter Championship " << endl;
		std::cout << "6: Quit" << endl;
		cin >> choice;

		if (choice == 1)
		{
			std::cout << "Enter Your First Name: " << endl;
			cin >> FirstName;
			std::cout << "Enter Your Last Name: " << endl;
			cin >> playerName;
			std::cout << "Enter Your Weight: " << endl;
			cin >> weight;
			std::cout << "Enter Your Boxing Number: " << endl;
			cin >> champNum;

			BoxerFile << "Full Name: " << FirstName << " " << playerName << "\n";
			BoxerFile << "Match Name: " << playerName << "\n";
			BoxerFile << "Weight: " << weight << "\n";
			if (weight < 150)
			{
				BoxerFile << "Weight Class: LightWeight" << "\n";
			}
			else if (weight > 150 && weight < 250)
			{
				BoxerFile << "Weight Class: MidWeight" << "\n";
			}
			else if (weight > 250)
			{
				BoxerFile << "Weight Class: HeavyWeight" << "\n";
			}
			BoxerFile << "Boxing Number: " << champNum << "\n";

		}
		else if (choice == 2)
		{
			ifstream rulesFile;
			rulesFile.open("Text1.txt");
			if (rulesFile.is_open())
			{
				while (!rulesFile.eof())
				{
					getline(rulesFile, line);
					cout << line << endl;
				}
			}
		}
		else if (choice == 3)
		{
			shop();

		}
		else if (choice == 4)
		{

			if (G1D == true)
			{
				cout << "You Own Gloves 1D With 25 Extra Damage!" << endl;
			}
			if (G2D == true)
			{
				cout << "You Own Gloves 2D With 50 Extra Damage!" << endl;
			}
			if (G3D == true)
			{
				cout << "You Own Gloves 3D With 75 Extra Damage!" << endl;
			}
			if (P1H == true)
			{
				cout << "You Own Purchase 1H With 25 Extra Stamina!" << endl;
			}
			if (P2H == true)
			{
				cout << "You Own Purchase 2H With 50 Extra Stamina!" << endl;
			}
			if (P3H == true)
			{
				cout << "You Own Purchase 3H With 75 Extra Stamina!" << endl;
			}
			if (P4H == true)
			{
				cout << "You Own Purchase 4H With 100 Extra Stamina!" << endl;
			}
		}
		else if (choice == 5)
		{

			int compBlock, compAttack;
			int attackMove, blockMove;
			srand(time(0));
			int compStamina, userStamina, userDamage;
			userStamina = User.getStamina();

			char HorT;
			int FightOutcome;
			User.setDamage(damage);
			User.setStamina(stamina);
			int C = 0;
			C = rand() % 10;
			string OpponentA;
			OpponentA = nameArray[C];
			cout << endl << endl << endl << endl << endl << endl;
			cout << "Your Opponent Is " << OpponentA << endl;
			cout << endl;
			cout << "========================================================= " << endl;
			cout << "Your Damage Is: " << User.getDamage();
			cout << "                ";
			cout << "Your Stamina Is: " << User.getStamina();
			cout << endl;
			cout << "========================================================= " << endl;
			cout << "You Get To Choose Coin Side, Would You Like Heads(H) Or Tails(T): " << endl;
			cin >> HorT;
			cout << HorT << " Has WON!!" << endl;
			do
			{
				compBlock = rand() % 2 + 1;
				compAttack = rand() % 2 + 1;
				cout << "Would You Like To Punch (1) Or Kick(2): ";
				cin >> attackMove;
				cout << endl;
				int userdam = User.getDamage();
				Comp.setDefenseMove(attackMove, compBlock, userdam);
				compStamina = Comp.getStamina();
				FightOutcome = Comp.FightResult();
				if (FightOutcome == 1)
				{
					cout << OpponentA << " Has Been Kicked!" << endl;
					cout << OpponentA << " Stamina: " << compStamina << endl;
					cout << endl;
				}
				else if (FightOutcome == 2)
				{
					cout << OpponentA << " Has Blocked Your Punch!" << endl;
					cout << OpponentA << " Stamina: " << compStamina << endl;
					cout << endl;
				}
				else if (FightOutcome == 3)
				{
					cout << OpponentA << " Has Been Punched!" << endl;
					cout << OpponentA << " Stamina: " << compStamina << endl;
					cout << endl;
				}
				else if (FightOutcome == 4)
				{
					cout << OpponentA << " Has Blocked Your Kick!" << endl;
					cout << OpponentA << " Stamina: " << compStamina << endl;
					cout << endl;
				}
				cout << "Would You Like To Block Upper Body(1) Or Lower Body(2): ";
				cin >> blockMove;
				cout << endl;
				User.setDefenseMove(compAttack, blockMove, userStamina);
				User.getStamina();
				FightOutcome = User.FightResult();
				if (FightOutcome == 1)
				{
					cout << "You Have Been Kicked!" << endl;
					cout << "Your Stamina: " << User.getStamina() << endl;
					cout << endl;
				}
				else if (FightOutcome == 2)
				{
					cout << "You Have Blocked " << OpponentA << "'s Punch!" << endl;
					cout << "Your Stamina: " << User.getStamina() << endl;
					cout << endl;
				}
				else if (FightOutcome == 3)
				{
					cout << " You Have Been Punched!" << endl;
					cout << "Your Stamina: " << User.getStamina() << endl;
					cout << endl;
				}
				else if (FightOutcome == 4)
				{
					cout << "You Have Blocked " << OpponentA << "'s Kick!" << endl;
					cout << "Your Stamina: " << User.getStamina() << endl;
					cout << endl;
				}
	

			} while (User.getStamina() > 0 && Comp.getStamina() > 0);

			if (User.getStamina() <= 0)
			{
				cout << "You Lost The Championship!" << endl;
				Win = true;
			}
			else if (Comp.getStamina() <= 0)
			{
				cout << "You Won the Championship!" << endl;
				Win = true;
			}


		}
		else if (choice == 6)
		{
		Win = true;
		}
		
	}while (Win != true);
	return 0;
}


