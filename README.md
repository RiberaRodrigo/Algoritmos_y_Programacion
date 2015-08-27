// EcuacionCuadratica

//Librerias
#include "stdafx.h"
#include "conio.h"
#include "math.h"
#include <string>
#include <iostream>

using namespace std;

//Cabeceras
void EcuacionCuadratica(float a, float b, float c, float &X1, float &X2);

// Principal
void main()
{
	float a, b, c, X1=0, X2=0;

	cout << "Ingresar valor para a: " << endl;
	cin >> a;
	cout << "Ingresar valor para b: " << endl;
	cin >> b;
	cout << "Ingresar valor para c: " << endl;
	cin >> c;
	
	EcuacionCuadratica(a, b, c , X1, X2);

	cout << "El Resultado para X1 es: " << X1 << endl;
	cout << "El Resultado para X2 es: " << X2 << endl;

	getch();
}

// Funciones
void EcuacionCuadratica(float a, float b, float c, float &X1, float &X2)
{
	if ((b*b) - 4*a*c > 0)
	{
		X1 = (-b + sqrt(b*b - 4*a*c)) / (2*a);
		X2 = (-b - sqrt(b*b - 4*a*c)) / (2*a);
	}
	else
		cout << "\n EL RESULTADO ES IMAGINARIO.\n\n\n";
}
