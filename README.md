# Algoritmos_y_Programacion
#include "stdafx.h"
#include <iostream>
#include "conio.h"
#include <string>
#include "stdlib.h"

#define MAX 100 //Declarar una constante por compilador
#define SM 1440

struct t_planilla
{
	int codigo;
	float SB;
	float dAFP;
	float dIVA;
	float dADIC;
	float SN;
	string nombre;
};

using namespace std;

float impuesto (t_planilla planilla);
float AFP (t_planilla planilla);
float promedio(t_planilla planilla,int tam);
//int mayor(float sn[],int tam);
//int menor(float sn[],int tam);

void main ()
{
	int i=0, num;
	float A[MAX];
	t_planilla planilla[MAX];
	do {
		cout << "Ingrese numero de empleados:";
		cin >> num;
		} while ((num>MAX)||(num<=0));
//ciclo repetitivo
	for (int i=0;i<num;i++)
	{do {
		cout<<"Ingrese el codigo del empleado: \n";
		cin>>planilla[i].codigo;
		}while(((planilla[i].codigo<=0)||(planilla[i].codigo>=200)));
// Ingreso de teclado de un string
		cout<<"Ingrese el nombre: ";
		getline(cin, planilla[i].nombre);
		do
		{
			cout <<"Ingrese el salario bruto: \n";
			cin>>planilla[i].SB;
		}while ((planilla[i].SB<=0)||(planilla[i].SB>=16000));
		if(planilla[i].SB > (SM*2) )
		{
			planilla[i].dIVA = impuesto(planilla[i].SB);
			planilla[i].dAFP = AFP(planilla[i].SB);
			planilla[i].SN = planilla[i].SB - planilla[i].dIVA - planilla[i].dAFP;
			if(planilla[i].SB > 15000)
			{
				A[i]=0.01*planilla[i].SB;
				planilla[i].SN = planilla[i].SN - A[i];
			}
			else
				A[i]=0;
		}
		else
		{
			planilla[i].dIVA=0;
			planilla[i].dAFP=0;
			A[i]=0;
			planilla[i].SN = planilla[i].SB;
		}
	}
	cout<<"------Planilla de sueldos-----"<<"\n";
	cout<<"Codigo"<<"\t"<<"Nombre"<<"\t";
	cout<<"Sal.Bruto"<<"\t"<<"Impuestos"<<"\t";
	cout<<"Afp"<<"\t"<<"Otro"<<"\t"<<"Sal.Neto"<<"\n";
	for(int c=0;c<num;c++)
	{ 
		cout<<planilla[c].codigo<<"\t"<<planilla[c].nombre<<"\t"<<planilla[c].SB<<"\t";
		cout<<planilla[c].dIVA<<"\t"<<planilla[c].dAFP<<"\t"<<A[c]<<"\t"<<planilla[c].SN<<"\n";
	}
	cout<<"Promedio de salario neto: "<<promedio(planilla.SN,num);
//	int m=mayor(planilla.SN,num);
//	int men=menor(planilla.SN,num);
//	cout<<"Mayor salario: "<<nombre[m]<<" con el salario: "<<sn[m];
//	cout<<"Menor salario: "<<nombre[men]<<" con el salario: "<<sn[men];
	cout<<"\n\nGracias \n";
	getch();
}

float impuesto (t_planilla planilla)
{return planilla.SB*0.13;
}
float AFP (t_planilla planilla)
{return planilla.SB*0.121;
}
float promedio(float sn[],int tam)
{
	int i;
	float prom, suma=0;
	for (i=0;i<tam;i++)
		suma=suma+sn[i];
	prom=suma/tam;
	return prom;
}
/*int mayor(float sn[],int tam)
{
	float may=0;
	int pos;
	for (int i=0;i<tam;i++)
		if (may<sn[i])
		{
			may=sn[i];
			pos=i;
		}
	return pos;
}
int menor(float sn[],int tam)
{
	float men=sn[0];
	int pos=0;
	for (int i=1;i<tam;i++)
		if (men>sn[i])
		{
			men=sn[i];
			pos=i;
		}
	return pos ;
}
*/
