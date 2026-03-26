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

cout << "Desea añadir otro significado?\n";
cout << "1. Si\n2. No\n";
cin >> anadirpal;

if (anadirpal == 1)
{
    cout << "Digite el significado 2: ";
    cin >> nuevo->significado2;

    cout << "Desea añadir otro significado?\n";
    cout << "1. Si\n2. No\n";
    cin >> anadirpal;

    if (anadirpal == 1)
    {
        cout << "Digite el significado 3: ";
        cin >> nuevo->significado3;
    }
}

cout << "La palabra fue guardada con exito\n";
}


int main()
{
    int op;
    long cod;

    do
    {
        cout << "\nBienvenidos al Programa de Administracion del Curso\n";
        cout << "1. Adicionar Palabra\n";
        cout << "2. Consultar Palabra\n";
        cout << "3. Editar Palabra\n";
        cout << "4. Eliminar Palabra\n";
        cout << "5. Imprimir Diccionario al derecho\n";
        cout << "6. Imprimir Diccionario al revés\n";
        cout << "7. Salir\n";
        cout << "Seleccione una opcion: ";
        cin >> op;

        switch (op)
        {
            case 1:
                cout << "Codigo del estudiante: ";
                cin >> cod;
                if (buscarest(cod))
                    cout << "El estudiante ya existe\n";
                else
                    capturarest(cod);
                break;
            case 2:
                cout << "Codigo del estudiante: ";
                cin >> cod;
                imprimirdatos(cod);
                break;
            case 3:
                cout << "Codigo del estudiante a editar: ";
                cin >> cod;
                editarest(cod);
                break;
            case 4:
                cout << "Codigo del estudiante a eliminar: ";
                cin >> cod;
                eliminarest(cod);
                break;
            case 5:
                cocktailsort();
            break;
            case 6:
                calculardef();
            break;
            case 7:
                visualizarest();
                calcularprom();
            break;
            case 8:
                cout << "Gracias por usar el programa\n";
            break;
            default:
                cout << "Opcion invalida\n";
        }
    } while (op != 8);

    liberarMemoria();
    return 0;
}
