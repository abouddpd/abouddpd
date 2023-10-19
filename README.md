#include <iostream>
#include <cmath>
#include <string>
using namespace std;
enum enrandoom { smallletters = 1, capitalletter = 2, specialcharacter = 3, digit = 4 };
int printrandoomnumber(int from, int to)
{
	int randoom = rand() % (to - from + 1) + from;
	return randoom;
}
char getrandoomcharacter(enrandoom enchar)
{
	
	switch (enchar)
	{
	case enrandoom::smallletters:
		return char(printrandoomnumber(97,122));
		break;
	case enrandoom::capitalletter:
		return char(printrandoomnumber(65, 90));
		break;
	case enrandoom::specialcharacter:
		return char(printrandoomnumber(33, 47));
		break;
	case enrandoom::digit:
		return (printrandoomnumber(48, 57));
		break;
	}


	
}


int readkeys()
{
	int key = 0;
	cout << "please enter how many keys do you want to generate : " << endl;
	cin >> key;
	return key;
}
string generateword()
{
	string word = "";

	for (int i=0;i<4;i++)
	{
		word = word + getrandoomcharacter(enrandoom::capitalletter);
	}
	return word;
}
string generatekey()
{
	string fullkey = generateword() + "-" + generateword() + "-" + generateword() + "-" + generateword();
	return fullkey;
}

void printresult(int key)
{
	for (int i=1;i<=key;i++)
	{
		cout << " key["<< i << "]" << "" << generatekey() << endl;
	}
}

int main()
{
	srand((unsigned)time(NULL)); 
	
	printresult(readkeys());
	return 0;
}
