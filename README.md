# reminderss
#include <iostream>
using namespace std;

int getInputDays()
{
	int inputDays = 0;
	bool validInput = false;
	while (validInput == false)
	{
		cout << "\n Please Enter Number of Days in a Month: ";
		cin >> inputDays;

		if (inputDays >= 28 && inputDays <= 31)
			validInput = true;
	}
	return inputDays;
}

int getInputOffset()
{
	int inputOffset = 0;
	bool validInput = false;
	while (validInput == false)
	{
		cout << "\n Please Enter the Offset Day (0 for Monday - 6 for Sunday): ";
		cin >> inputOffset;

		if (inputOffset >= 0 && inputOffset <= 6)
			validInput = true;
	}

	if (inputOffset == 6)
		inputOffset = 0;
	else
		inputOffset += 1;
	return inputOffset;
}

void displayOffset(int offset)
{
	if (offset == 1)
		cout << "       1";
	else if (offset == 2)
		cout << "           1";
	else if (offset == 3)
		cout << "              1";
	else if (offset == 4)
		cout << "                   1";
	else if (offset == 5)
		cout << "                       1";
	else
		cout << "                           1";
}

void drawCalendar(int days, int offset)
{
	int date = 1;
	int spaces = 0;
	cout << "\n\n\t C A L E N D A R\n\n  Su  Mo  Tu  We  Th  Fr  Sa" << endl;
	while (date <= days)
	{
		if (offset > 0)
		{
			displayOffset(offset);
			date = 2;
			spaces = (offset * 4) + 4;
			offset = 0;
		}
		while (spaces < 28)
		{
			if (date >= 10)
			{
				if (date > days)
					break;
				cout << "  " << date;
			}
			else
				cout << "   " << date;
			date += 1;
			spaces += 4;
		}
		cout << endl;
		spaces = 0;
	}
}

int main()
{
	int days = getInputDays();
	int offset = getInputOffset();

	drawCalendar(days, offset);

	cout << endl;
	
	return 0;
}
