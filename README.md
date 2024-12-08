# it1314-lab
#include <iostream>
#include <fstream>
#include <string>
#include <iomanip>
#include <cmath>
#include <windows.h>

using namespace std;

void ran(int** A, int N, int M)
{
	srand(time(0));

	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < M; j++)
		{
			A[i][j] = (rand() % 201) - 100;
		}
	}
}

void cons(int** A, int N, int M)
{
	int b;

	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < M; j++)
		{
			cin >> b;
			A[i][j] = b;
		}
	}

	cout << endl;
}

void file(int** A, int N, int M)
{
	int i = 0;
	ifstream f;
	f.open("C:\\Задания\\psu\\lab 8\\1b.txt", ios::in);

	if (f.is_open())
	{
		while (!f.eof())
		{
			for (int i = 0; i < N; i++)
			{
				for (int j = 0; j < M; j++)
				{
					f >> A[i][j];
				}
			}
		}
	}
	f.close();
}

void func(int** A, int N, int M)
{
	int min = 10000, max = -10000, s1, s2, r1, r2, t1, t2;
	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < M; j++)
		{
			if (A[i][j] > max)
			{
				max = A[i][j];
			}
			if (A[i][j] < min)
			{
				min = A[i][j];
			}
		}

	}

	int min2 = 10000, max2 = -10000;
	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < M; j++)
		{
			if (A[i][j] > max2)
			{
				max2 = A[i][j];
				r1 = i;
				r2 = j;
			}
			else if (A[i][j] < min2)
			{
				min2 = A[i][j];
				t1 = i;
				t2 = j;
			}
		}
	}

	cout << "Максимальный элемент -> " << max << " , минимальный элемент -> " << min << endl;

	if (A[0][0] == min and A[N - 1][M - 1] == max)
	{
		s1 = A[0][0];
		A[0][0] = max;
		A[N-1][M-1] = s1;
	}
	else if (A[0][0] == max and A[N - 1][M - 1] == min)
	{
		A[0][0] == max;
		A[N - 1][M - 1] == min;
	}
	else if ((A[0][0] == min and A[N - 1][0] == max) or (A[0][0] == max and A[N - 1][0] == min))
	{
		swap(A[0][0], A[r1][r2]);
		t1 = r1;
		t2 = r2;
		swap(A[N - 1][M - 1], A[t1][t2]);
	}
	else if ((A[0][0] == min and A[0][M - 1] == max) or (A[0][0] == max and A[0][M-1] == min))
	{
		swap(A[0][0], A[r1][r2]);
		t1 = r1;
		t2 = r2;
		swap(A[N - 1][M - 1], A[t1][t2]);
	}
	else
	{
		swap(A[0][0], A[r1][r2]);
		swap(A[N - 1][M - 1], A[t1][t2]);
	}
}

int main()
{
	setlocale(LC_ALL, "RU");
	SetConsoleCP(1251);
	SetConsoleOutputCP(1251);

	int number, N, M;
	cout << "Количество строк - ";
	cin >> N;
	cout << "Количество столбцов - ";
	cin >> M;

	int** A = new int* [N];
	for (int p = 0; p < N; p++)
	{
		A[p] = new int[M];
	}

	cout << "Выбирите способ заполнения массива: " << endl;
	cout << "1)Случайно" << endl;
	cout << "2)Вручную" << endl;
	cout << "3)Файл" << endl;
	cout << ">>> ";
	cin >> number;

	if (number == 1)
	{
		ran(A, N, M);
	}
	else
	{
		if (number == 2)
		{
			cons(A, N, M);
		}
		else
		{
			file(A, N, M);
		}

	}

	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < M; j++)
		{
			cout << A[i][j] << "\t";
		}
		cout << endl;
	}

	cout << " " << endl;
	func(A, N, M);
	for (int i = 0; i < N; i++)
	{
		for (int j = 0; j < M; j++)
		{
			cout << A[i][j] << "\t";
		}
		cout << endl;
	}


}
