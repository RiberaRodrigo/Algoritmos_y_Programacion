# Algoritmos_y_Programacion
//Kareminfantas@gmail.com
//gisela gilbert aldana
//Rodrigo Ribera Riojas
#include "stdafx.h"
#include <iostream>
#include "conio.h"
#include <string>
#include "stdlib.h"

using namespace std;

#define FIL 10
#define COL 10
#define MAX 30

struct t_Vector{
	int Matriz[FIL][COL];
};
t_Vector Vec[MAX];

void Cargar(t_Vector Mat[FIL][COL], int n);
void Mostrar(t_Vector Mat[FIL][COL], int n);
void Ordenar(int Vect[MAX], int n);
void Obtener(t_Vector Mat[FIL][COL], int n);

void main()
{
	int n;
	t_Vector Mat[FIL][COL];
	do{
		cout << "\n\n\n Ingrese el numero de elementos: ";
		cin >> n;
		cout << endl;
	}while(n<=0 || n>10);

	Cargar(Mat,n);
	Mostrar(Mat,n);
	cout << endl;
	Obtener(Mat,n);

	getch();
}

void Cargar(t_Vector Mat[FIL][COL], int n)
{
	int i, j, k;
	for(i=0; i < n; i++)
		for(j=0; j < n; j++)
			for(k=0; k < n; k++)
				{
					/*cin >>*/ Vec[k].Matriz[j][i] = rand() %10;
				}
}


void Mostrar(t_Vector Mat[FIL][COL], int n)
{
	int i, j, k;
	for(i=0; i < n; i++)
	{
		for(j=0; j < n; j++)
		{
			for(k=0; k < n; k++)
			{
				cout << "["<<i<<"]["<<j<<"].["<<k<<"]= " << Vec[k].Matriz[j][i] <<"\t";
			}
			cout << endl;
		}
		cout << endl;
	}
}

void Ordenar(int Vect[MAX], int n)
{
	int i, j, aux;
	for(i=0; i < n-1; i++)
		for(j=1; j < n; j++)
		{
			if(Vect[i] > Vect[j])
			{
				aux = Vect[i];
				Vect[i] = Vect[j];
				Vect[j] = aux;
			}
		}

}

// (3,0) (0,1) (3,2) (0,3)
void Obtener(t_Vector Mat[FIL][COL], int n)
{
	int i, j, k, Vaux[MAX], N;
		for(i=0; i < n; i++)
				Vaux[i] = Vec[i].Matriz[0][3];
		k=0;
		for(i+1; i < n*2; i++)
			{
				Vaux[i] = Vec[k].Matriz[1][0];
				k++;
			}
		k=0;
		for(i+1; i < n*3; i++)
			{
				Vaux[i] = Vec[k].Matriz[2][3];
				k++;
			}
		k=0;
		for(i+1; i < n*4; i++)
			{
				Vaux[i] = Vec[k].Matriz[3][0];
				k++;
			}
		for(i=0; i < n*4; i++)
			cout << Vaux[i] << "  ";
		N = n*4;
		Ordenar(Vaux,N);
		cout << endl;
		for(i=0; i < N; i++)
			cout << Vaux[i] << "  ";
		
}
