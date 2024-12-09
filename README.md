# it1314-lab
#include <iostream>
#include "windows.h"

using namespace std;

int RandNumber(int a, int b){
    int c;
    c = b - a;
    return rand() % c + a;
}

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
    int A, B, CNT, NUMBER = 0, r = 1, n;
    cout << "Игра угадайка." << endl << endl;

    while (r == 1)
    {
        cout << "Введите диапазон от n до k (n < k) в котором будет загадываться число:" << endl;
        cin >> A >> B;
        NUMBER = RandNumber(A, B);
        CNT = Play(NUMBER, A, B);
        cout << "Вы угадали!!!" << endl;
        cout << "Общее количество попыток - " << CNT << endl << endl;
        cout << "Хотите сыграть ещё раз?" << endl;
        cout << "Если да введите 1, если нет, то введите 0" << endl;
        cin >> r;

    }

}
