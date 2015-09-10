# Algoritmos_y_Programacion
#include "stdafx.h"
#include "conio.h"
#include <iostream>
#include <string>
#include "math.h"
#include "stdlib.h"
#define TAM 50

using namespace std;

void cargar_vector(int A[], int n);
void cargar_vectors(string nombre[], int n);
void mostrar_vector(int A[], int n);
void ordenar_vector(int A[], int n);
int busqueda_binaria(int A[], int n, int k);
void arrays_paralelos(string nombre[], int nota[], int n);
void mostrar_paralelos(string nombre[], int nota[], int n);


void main ()
{
	int op, n, sol, a,b, A[TAM], z, clave;
	string nombre[TAM];

	do
	{
		cout<<"1 . Cargar Vector Entero "<<endl;
		cout<<"2 . Cargar Vector String "<<endl;
		cout<<"3 . Mostrar Vector Entero "<<endl;
		cout<<"4 . Clasificar Vector Paralelo "<<endl;
		cout<<"5 . Mostrar Vector Paralelo "<<endl;
		cout<<"6 . Busqueda Binaria "<<endl;
		cout<<"0 . Salir"<<endl;
		
		cout <<"Ingrese la opcion: ";
		cin>>op;

		switch (op)
		{
		case 1: do {
					cout<<"ingrese el numero de elementos: ";
					cin>>n;
				}
				while ((n>TAM) || (n<0));
				cargar_vector(A,n);
				break;

		case 2: do {
					cout<<"ingrese el numero de elementos : ";
					cin>>n;
				}
				while ((n>TAM) || (n<0));
				cargar_vectors(nombre,n);
				break;

		case 3: 
				mostrar_vector(A,n);
				break;

		case 4: 
				arrays_paralelos(nombre, A, n);
				break;

		case 5: 
				mostrar_paralelos(nombre, A, n);
				break;
				
		case 6:
				cout << "Ingrese el numero a buscar: ";
				cin >> clave;
				z=busqueda_binaria(A, n, clave);
				if(z == -1)
					cout << "\nEl numero no existe en el vector"<< endl;
				else
					cout<<"\nEl numero "<< A[z] << "esta en la posicion: " << z;
				break;

		case 7:
				clasificacion_insercion(A, n);
				break;
				
		case 0:
				cout<<"Fin del programa";
				break;

		default:
				cout<<"Opcion invalida :";
				break;
		}
		getch();
		system("cls");
	}while (op!=0);
	getch();
}

void cargar_vector(int A[], int n)
{
	for (int i=0; i<n; i++)
	{
		cout<<"A["<<i<<"] = ";
		cin>>A[i];
	}
}

void cargar_vectors(string nombre[], int n)
{
	cin.ignore();
	for (int i=0; i<n; i++)
	{
		cout<<"Nombre["<<i<<"]= ";
		getline(cin, nombre[i]);
	}
}

void mostrar_vector(int A[], int n)
{
	for (int i=0; i<n; i++)
	{
		cout<<"A["<<i<<"] = "<<A[i]<<endl;
	}
}

int busqueda_binaria(int A[], int n, int k)
{
  int fin = n-1,ini = 0,medio;
  while (ini <= fin)
    {
      medio = (fin + ini)/2;
      if (A[medio] == k)
         return medio;
      else
         if (k < A[medio])
            fin=medio-1;
         else
            ini=medio+1;
    }
  return -1;
}

void arrays_paralelos(string nombre[], int nota[], int n)
{
	int aux;
	string auxs;
	for (int i=0; i< n-1; i++)
		for (int j=i+1; j<n; j++)
			if (nota[i] > nota[j])
			{
				aux=nota[j];
				nota[j]=nota[i];
				nota[i]=aux;
				auxs=nombre[j];
				nombre[j]=nombre[i];
				nombre[i]=auxs;

			}
}

void mostrar_paralelos(string nombre[], int nota[], int n)
{
	cout<<"No. \t Nombre y Apellido \t Nota"<<endl;
	cout<<"---------------------------------------"<<endl;
	for (int i=0; i<n; i++)
		cout<<i+1<<"	"<<nombre[i]<<"			"<<nota[i]<<endl;
}

void clasificacion_insercion(int A[], int n)
{
	int aux;
	cout << "Ingrese Numero de elementos: ";
	cin >> n;
	for(int i = 0 : i < n; i++)
	{
		cargar_vector(A[i], n);
		aux = A[i];
		for(int j = i+1; j < n-1; j++)
			if (A[i]<=aux)
			{
				A[i] = A[j];
			}
		cout << "	"; 
		mostrar_vector(A[i], n);
	}
}
