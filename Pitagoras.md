//Grupo#3
Python
#Encuentre todos los triples de Pitágoras para lado1, lado2, y la hipotenusa, que no sean mayores de 500.
a=0
b=a+1
#importamos librería math
import math
print("bienvenid@, ingrese 2 numeros enteros")
#declaramos variables a y b
a =int(input("Ingrese #1: "))
b= int(input("Ingrese #2: "))
#Nos muestra en consola la diferencia de cuadrados del triple pitagórico
print (a**2 - b**2)
#El cateto b estará entre el rango de 1 a 500
for b in range(1,500):
  for c in range(b,500):
    #Nos muestra en consola la suma de cuadrados del triple pitagórico.
    a=math.sqrt(b**2+c**2)
    if a == int(a):
      print(b,c,int(a))
      print("adiós")

C++
//Programa triple de pitagoras_establece que la suma de los cuadrados de dos lados es igual al cuadrado de la hipotenusa
#include <iostream>
#include <stdio.h>
#include <math.h>

using namespace std;

int main()
{
    int a, b, c, suma, h2;//Variables de inicio  
    float ladoa, ladob, hipoc; 
    
    for (a=b=c=1, suma=0; c<=500; ++c){ 
        
        hipoc=pow(c,2);
        
        while(a<=c){
            ladoa=pow(a,2); //pow función que retorna la base elevada al exponente
            
            while(suma<=hipoc){
                ladob=pow(b,2);
                suma=ladoa+ladob; //la suma de los lados
                ++b;
                if(suma==hipoc){
                    ladoa=sqrt(ladoa); //sqrt función que devuelve la raíz cuadrada de un valor numérico 
                    ladob=sqrt(ladob);
                    hipoc=sqrt(hipoc);
                    cout << "Lado a: " << ladoa << "    Lado b: " << ladob << "    Hipotenusa: " << hipoc << "\n";
                }
                break; 
            }
            
            ++a;
            b=h2=1;
            ladoa=pow(a,2);
            ladob=pow(b,2);
            suma=ladoa+ladob;
           
        }
        
        a=1;
        suma=0;
    }

    return 0; //finalización del programa 
}

Pseudocodigo

algoritmo pitagoras
Escribir Sin Saltar "Ingresa el valor de a:";
    Leer a;
    Escribir Sin Saltar "Ingresa el valor de b:";
    Leer b;
    Escribir "Selecciona el valor de operacion.";
    Escribir "    1.- Ángulo";
    Escribir "    2.- Hipotenusa";
    Escribir "    3.- Cateto opuesto";
    Escribir "    4.- Cateto adyacente";
    Escribir Sin Saltar "    :";
    Repetir
        Leer operacion;
        Si operacion<1 O operacion>4 Entonces
            Escribir Sin Saltar "Valor incorrecto. Ingrésalo nuevamente.: ";
        FinSi
    Hasta Que operacion>=1 Y operacion<=4;
    resultado <- 0;
    Si operacion = 1 Y b <> 0 Entonces
        resultado <- ATAN(a/b)*180.0/PI;
    FinSi
    Si operacion = 1 Y b = 0 Entonces
        Escribir "Error";
    FinSi
    Si operacion = 2 Entonces
        resultado <- RC(a*a+b*b);
    FinSi
    Si operacion = 3 Y a>=b Entonces
        resultado <- RC(a*a-b*b);
    FinSi
    Si operacion = 3 Y a<b Entonces
        Escribir "Error";
    FinSi
    Si operacion = 4 Y b>=a Entonces
        resultado <- RC(b*b-a*a);
    FinSi
    Si operacion = 4 Y b<a Entonces
        Escribir "Error";
    FinSi
    Escribir "Valor de resultado: ", resultado;
FinProceso