#include <iostream>
#include <string>

using namespace std;

struct diccionario
{
    string palabra, significado1, significado2, significado3,;
    diccionario* siguiente; 
};


diccionario* inicio = nullptr; 
bool palabraexis = false;
int añadir;


bool buscarest(long buscar)
{
    diccionario* actual = inicio; 

    while (actual != nullptr)
    {
        if (actual->palabra == buscar)
            return true;

        actual = actual->siguiente; 
    }

    return false;
}


void capturarpal(long buscar)
{
    diccionario* nuevo = new diccionario();

    nuevo->palabra = buscar;

    cin.ignore();
    cout << "Digite la palabra que desea añadir: ";
    getline(cin, nuevo->palabra);

        cout << "Digite el significado 1: ";
        cin >> nuevo->significado1;
        cout << "Desea añadir otra palabra?";
        cout << "1. Si \n";
        cout << "2. No \n";
        cin >> añadirpal
        if (nuevo->corte1 < 1.5 || nuevo->corte1 > 5)
            cout << "Nota fuera del rango, intente nuevamente\n";

    do
    {
        cout << "Digite el significado 2: ";
        cin >> nuevo->corte2;
        if (nuevo->corte2 < 1.5 || nuevo->corte2 > 5)
            cout << "Nota fuera del rango, intente nuevamente\n";
    } while (nuevo->corte2 < 1.5 || nuevo->corte2 > 5);

    do
    {
        cout << "Digite el significado 3: ";
        cin >> nuevo->corte3;
        if (nuevo->corte3 < 1.5 || nuevo->corte3 > 5)
            cout << "Nota fuera del rango, intente nuevamente\n";
    } while (nuevo->corte3 < 1.5 || nuevo->corte3 > 5);

    nuevo->def = 0;


    nuevo->siguiente = inicio; 
    inicio = nuevo;

    cout << "Estudiante agregado con exito\n";
}
