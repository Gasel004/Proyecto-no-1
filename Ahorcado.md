//Grupo#3

pseudocodigo
//Algoritmo que emule el juego de ahorcado teniendo escondidas ciertas palabras para que el usuario no sepa cuales son.
//El usuario contara con 6 intentos estos correspondiente a las partes del cuerpo para simular el dibujo de una persona ahorcada
Algoritmo ejercicio_2_Proyecto_1
	Escribir "*** Bienvenido al juego del ahorcado ***"
	Escribir "Suerte :) "
	//Definifmos las palabras que habran y las oportunidades que tendra para adivinar la palabra secreta.	
    Secretas <- 6;
    oportunidades <- 6;
    Dimension palabras[Secretas];
    palabras[1] <- "Supernova";
    palabras[2] <- "Siddhartha";
    palabras[3] <- "Fuego";
    palabras[4] <- "Capo";
    palabras[5] <- "Valor";
    palabras[6] <- "Admirador";
	cabeza <- ' ';
    cuerpo <- ' ';
    mano_izquierda <- ' ';
    mano_derecha <- ' ';
    pie_izquierdo <- ' ';
    pie_derecho <- ' ';
    turnos <- 0;
    aciertos <- 0;
//El programa escoje la palabra secreta para que el usuario siga desconociendo cual es
    palabra <- palabras[Azar(Secretas)+1];
    n <- Longitud(palabra);
    Dimension casillas(n);
//Cada letra se guardara
    Para i<-1 Hasta n Con Paso 1 Hacer
        casillas[i] <- '_';
    FinPara
    Repetir
        Escribir "";
//Mostramos el mensaje de cauntos intentos le quedan al usuario
        Escribir "Intentos restantes: ", oportunidades-turnos;
        Para i<-1 Hasta n Con Paso 1 Hacer
            Escribir Sin Saltar " ", casillas[i];
        FinPara
        Escribir "";
//Volvemos a pedir al usuario que ingrese otra letra
        Escribir Sin Saltar "Escriba una letra: ";
        Leer letra;
        encontrado <- Falso;
//Verificamos si existe o no en la palabra secreta 
        Para i<-1 Hasta n Con Paso 1 Hacer
            chr <- Subcadena(palabra, i, i);
            Si Mayusculas(letra)=Mayusculas(chr) Entonces
                encontrado <- Verdadero;
//Se almacena la letra si existe en la palbra
                Si casillas[i]='_' Entonces
                    casillas[i] <- chr;
                    aciertos <- aciertos+1;
                FinSi
            FinSi
        FinPara
		//Creamos la Funcion entonces para colocar las partes del cuerpo agregando una cada vez que la letra que ingrese el usuario no exista en la palabra que tenga que adivinar.
        Si No encontrado Entonces
            turnos <- turnos+1;
            Escribir "La letra no existe.";
            Segun turnos Hacer
                1:
                    Cabeza <- '(*_*)';
                2:
                    Cuerpo <- '+';
                3:
                    mano_derecha <- '/';
                4:
                    mano_izquierda <- '\';
                5:
                    pie_derecho <- '/';
                6:
                    pie_izquierdo <- '\';
            FinSegun
        FinSI
//Mostramos al usario las partes del cuerpo cada que elija una letra inexistente
        Escribir "   ", Cabeza," ";
        Escribir "    ", mano_derecha, Cuerpo, mano_izquierda;
        Escribir "    ", pie_derecho," ", pie_izquierdo;
        Escribir "";
//definimos hasta que los turnos sean menores a las oportunidades, mostrando lo siguiente;
    Hasta Que turnos>=oportunidades O aciertos>=n;
    Si aciertos=n Entonces
//El usuario acerto la palabra se le muestra lo siguiente;
        Escribir "¡¡¡ Felicidades, has ganado !!! :).";
    Sino
//El usuario fallo al adivianar, se le muetra lo siguiente;
        Escribir "¡ Has perdido! :(.";
		Escribir "Suerte para la proxima :)"
    FinSi
//Gane o pierda se le mostrara la palabra escondida, mostrandola así;
    Escribir "La palabra escondida es: ", palabra;
FinAlgoritmo

//(*_*)



Python
#Importamos el modulo ramdom para escojer una palabra de las que estan predeterminadamente aleatoriamente.
import random

#Definimos las palabras que guardaremos en secreto.
palabras = ["Supernova", "Siddharta", "Fuego", "Capo", "Valor", "Admirador"]
#Inicializamos la variable secretas dandole como valor "palabras"
secretas = len(palabras)
#Colocamos 6 oportunidades las cuales corresponden a las partes del cuerpo(cabeza, cuerpo, mano izquierda y derecha, pie izquierdo y derecho) para asi con los falles del usuario formar el ahorcado
oportunidades = 6
#Inicializamos las demas 
cabeza = ' '
cuerpo = ' '
mano_izquierda = ' '
mano_derecha = ' '
pie_izquierdo = ' '
pie_derecho = ' '
turnos = 0
aciertos = 0

#Inicimaos la funcion que importamos al inicio "random" para tomar aleatoriamente una palabra de las que ingresamos al principio tambien.
palabra = palabras[random.randint(0, secretas - 1)]
#Obtenemos la longitud de la palabra secreta y la guardamos en y
y = len(palabra)
#Creamos una lista para almacenar las letras ingresadas por el usuario sean acertadas o no
casillas = ['_' for _ in range(y)]


#Iniciamos un ciclo while que se repetira cuando el numero de turnos sea menor menor que las oportunidades y el numero de aciertos sea menor de la longitud de la palabra secreta.
#Asi mismos mostramos la cantidad de intentos restantes y el estado actual de la letras adivinadas por espacios separados.
print("Bienvenido al juego del ahorcado")
print("Suerte :)")
while turnos < oportunidades and aciertos < y:
    print()
    print(f"Intentos restantes: {oportunidades - turnos}")
    print(" ".join(casillas))
#Solicitamos al usuario que ingrese una letra.  
    letra = input("Escriba una letra: ")
#Aunque el usuario ingrese varias letras, el programa tomara la primera, gracias a la siguiente linea de codigo.
    letra = letra[0]     
    

#Inicializamos la variable encontrado como false 
    encontrado = False
#Iniciamos un ciclo for para que el programa verifique si la letra ingresada por el usuario exista o no en la palbra secreta.  
    for n in range(y):
        chr = palabra[n]
        if letra.upper() == chr.upper():
            encontrado = True
            if casillas[n] == '_':
                casillas[n] = chr
                aciertos += 1
#El bucle while seguira funcionando hasta que el usuario acierte todas las letras o se le acaben los intentos lo que suceda primero
#Si la letra ingresada por el usuario no es encontrada en la palabra secreta 
    if not encontrado:
        turnos += 1
        print("La letra no existe.")
#En caso de que la letra ingresada por el usuario no exista dentro de la palanbra secreta creamos una lista de sucesos correspondientes
#A 6 errores para ir colocando una parte del cuerpo cada vez que la letra no exista.
        if turnos == 1:
           cabeza = '(*_*)'
        elif turnos == 2:
             cuerpo = '+'
        elif turnos == 3:
             mano_derecha = '/'
        elif turnos == 4:
             mano_izquierda = '\\'
        elif turnos == 5:
             pie_derecho = '/'
        elif turnos == 6:
             pie_izquierdo = '\\'
#Imprimimos las partes del cuerpo con cada error del usuario
        print("    ", cabeza)
        print("    ", mano_derecha, cuerpo, mano_izquierda)
        print("     ", pie_derecho, pie_izquierdo)
        print()

if aciertos == y:
#Finalmente dependiendo de si el usurio gana o pierde se le mostrara unos de los 2 siguientes mensajes.
    print("¡¡¡ Felicidades, has ganado !!! :)")
else:
    print("¡ Has perdido! :(")

print("La palabra secreta era:", palabra)

#(*_*)



C++
//Iniciamos el codigo que simule el famosos juego del ahorcado. 
//Importamos la biblioteca basica para c++ (iostream) para manejar datos de entrada y salida.
//También importamos la libreria <string> para trabajar con cadenas de texto
//También la libreria <cstdlib> para trabajar con seleccion aleatoria más adelante.
#include <iostream>
#include <string>
#include <cstdlib>

//Utilizamos la estructura basica de C++.
using namespace std;
int main() {
//Inicializmos las variables que usaremos y a unas de ellas le daremos un valor a otras se les dara más adelante.
    int Secretas = 6;
    int oportunidades = 6;
//Agregamos una cadena de texto para almacenar las palabras que queremos mantener en secreto al usuario en este caso 7.
    string palabras[7];
    palabras[1] = "Supernova";
    palabras[2] = "Siddhartha";
    palabras[3] = "Fuego";
    palabras[4] = "Capo";
    palabras[5] = "Valor";
    palabras[6] = "Admirador";
//Inicializamos las variables del cuerpo humano que le daremos un valor más adelante
    char cabeza = ' ';
    char cuerpo = ' ';
    char mano_izquierda = ' ';
    char mano_derecha = ' ';
    char pie_izquierdo = ' ';
    char pie_derecho = ' ';
//También inicimos las variables de turnos y aciertos que tendran valor en un futuro del algoritmo.
    int turnos = 0;
    int aciertos = 0;
    
//Utilizamos la funcion rand para tomar una palabra aleatoria de las que definimos al principio.    
    srand(static_cast<unsigned int>(time(nullptr)));
    string palabra = palabras[rand() % Secretas + 1];
    int n = palabra.length();
//Creamos la longitud de la palabra seleccionada aleatoriamente por la función anterio representado a las letras con un guión bajo.
    char casillas[n];
    
    for (int i = 0; i < n; i++) {
        casillas[i] = '_';
    }
//Iniciamos un bucle el cual funcionara para verificar la letra ingresada por el usuario con las que representan la palabra secreta.
//Esto se repetira hasta que el usuario agote todas sus oportunidades (6)
    do {
        cout << "\n";
        cout << "Intentos restantes: " << oportunidades - turnos << endl;
        
//A medidada que el usuario siga ingresando letras se le mostrara su proceso con la palabra secreta y las oportunidades que aún le quedan.        
        for (int i = 0; i < n; i++) {
            std::cout << " " << casillas[i];
        }
        
        cout << "\n";
        cout << "Escriba una letra: ";
        char letra;
        cin >> letra;
        bool encontrado = false;
        
 //Con esta función se comprobra si la letra ingresada existe o no si existe se actualiza (casillas) e incrementa aciertos       
        for (int i = 0; i < n; i++) {
            char chr = palabra[i];
            if (toupper(letra) == toupper(chr)) {
                encontrado = true;
                if (casillas[i] == '_') {
                    casillas[i] = chr;
                    aciertos++;
                }
            }
        }
//Si la letra ingresada por el usuario es incorrecta ocurre lo siguiete con está función se incrementan los turnos y se agrega la parte del cuerpo correspondiente
//Hasta que las oportunidades se agoten se mostrará el cuerpo completo
        if (!encontrado) {
            turnos++;
            cout << "La letra no existe." << endl;
            switch (turnos) {
            	
//Segun el usuario siga errando con la selección de letras ocurriran los siguientes casos 1 por cada representación del cuerpo humano,
                case 1:
                    cabeza = 'O';
                    break;
                case 2:
                    cuerpo = '+';
                    break;
                case 3:
                    mano_derecha = '/';
                    break;
                case 4:
                    mano_izquierda = '\\';
                    break;
                case 5:
                    pie_derecho = '/';
                    break;
                case 6:
                    pie_izquierdo = '\\';
                    break;
            }
        }
//Así se mostrará el cuerpo a medida que las oportunidades vayan disminuyendo.      
        cout << "     " << cabeza << " " << endl;
        cout << "    " << mano_derecha << cuerpo << mano_izquierda << endl;
        cout << "    " << pie_derecho << " " << pie_izquierdo << endl;
        cout << endl;

    } while (turnos < oportunidades && aciertos < n);

//Gane o pierda el usuario dependiendo que pase primero mediante las decisiónes del usuario se le mostrará alguno de los 2 siguientes mensajes:
    if (aciertos == n) {
//El mensaje que se le mostrará si el usuario adivino la palabra secreta.
        cout << "¡¡¡ Felicidades, has ganado !!! :)" << endl;
    } else {
//El mensaje que se le mostrará si el usuario a perdido.
        cout << "¡ Has perdido! :(" << endl;
         cout <<"Suerte para la próxima :) "<< endl;
    }
//Gané o pierda el usario sin importare al programa se le mostrará el siguiente mensaje;
    cout << "La palabra escondida es: " << palabra << endl;

    return 0;
}


//(*_*)