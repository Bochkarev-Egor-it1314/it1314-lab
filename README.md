# it1314-lab
#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
#include <cmath>
#include <windows.h>

using namespace std;

int Play(int number, int a, int b){
    int cnt = 0, x = MAXINT;
    cout << "Теперь пытайтесь отгадать число в диапозоне от " << a << " до " << b << ":" << endl;
    while (x != number){
        cin >> x;
        cnt++;
        if (number < x) cout << "Число, которое я загадал, меньше " << x << endl;
        if (number > x) cout << "Число, которое я загадал, больше " << x << endl;
    }
    return cnt;
}

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
