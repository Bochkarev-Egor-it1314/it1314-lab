# it1314-lab
#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
#include <cmath>
#include <windows.h>

using namespace std;

int main()
{
    setlocale(LC_ALL, "Russian");
    srand(time(NULL));
    int A, B, CNT, NUMBER = 0;
    cout << "Игра угадайка." << endl << endl;
    cout << "Введите диапазон с котором бут загадываться число:";
    cin >> A >> B;
    NUMBER = RandNumber(A, B);
    CNT = Play(NUMBER, A, B);
    cout << "Вы угадали!!!" << endl;
    cout << "Общее количество попыток - " << CNT;
}
