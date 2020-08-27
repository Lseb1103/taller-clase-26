# taller-clase-26
#include <iostream>
#include <fstream>
using namespace std;
void llenar(int x, int valor1);
void buscar(int x, int valor1, int primero, int n);
int A[100];
int main()
{
  ofstream datos;
  datos.open("interpolacion.txt",ios::out);
  int x=0, valor1, primero=0, n=0;
  llenar(x,valor1);
  for(int i=0;i<x;i++)
  {
    datos<<A[i]<< endl;
  }
  cout << "ingrese el elemento a buscar: ";
    cin >> valor1;
    datos<<"elemento a buscar: "<< valor1 << endl;
  buscar(x,valor1, primero,n);
  if (A[primero]==n)
    {
        datos<<"ELEMENTO ENCONTRADO EN LA POSICION: "<< A[primero];
    }
    else
    {
         datos<<"ELEMENTO NO ENCONTRADO";
    }
    datos.close();
  return 0;
}
void llenar(int x, int valor)
{
  int tam;
  cout << "ingrese el tamaño: ";
  cin >> tam;
  while(x<tam)
  {
     cout << " valor: ";
     cin >> valor;
     A[x]=valor;
     x++;
  }
}
void buscar(int x, int valor1, int primero, int n)
{
    int ultimo = x-1;
    int medio;
     n=valor1;
    int contador=0;
    while (A[primero]!=n && contador < x)
    {

        medio = primero + ((n-A[primero])*(ultimo -primero))/(A[ultimo]-A[primero]);

        if(A[medio]<n)
            ultimo =medio+1;
        else if (A[medio]>n)
            ultimo = medio -1;
        else
            primero = medio;
        contador++;

        break;
    }

    if (A[primero]==n)
    {
        cout<<"ELEMENTO ENCONTRADO EN LA POSICION: "<< A[primero];
    }
    else
    {
         cout<<"ELEMENTO NO ENCONTRADO";
    }
}
