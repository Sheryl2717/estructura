#include <iostream>
#include <string>

using namespace std;

struct diccionario
{
    string palabra, significado1, significado2, significado3;
    diccionario* siguiente;
    diccionario* anterior;
};


diccionario* inicio = nullptr; 
bool palabraexis = false;
int anadirpal;
string buscar;


bool buscarpal(string buscar)
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


void capturarpal(string buscar)
{
    diccionario* nuevo = new diccionario();

    nuevo->palabra = buscar;

    cin.ignore();

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
        nuevo->siguiente = inicio;
nuevo->anterior = nullptr;

if (inicio != nullptr)
{
    inicio->anterior = nuevo;
}

inicio = nuevo;
        cout << "La palabra fue guardada con exito\n";
}


void imprimirpal(string buscar)
{
    diccionario* actual = inicio;

    while (actual != nullptr)
    {
        if (actual->palabra == buscar)
        {
            cout << "Palabra: " << actual->palabra << endl;
            cout << "Significado 1: " << actual->significado1 << endl;
            cout << "Significado 2: " << actual->significado2 << endl;
            cout << "Significado 3: " << actual->significado3 << endl;
            return;
        }
        
        actual = actual->siguiente;
    }

    cout << "La palabra no existe\n";
}


void editarpal(string buscar)
{
    diccionario* actual = inicio;

    while (actual != nullptr)
    {
        if (actual->palabra == buscar)
        {
            cout << "Significado 1: " << actual->significado1 << endl;
            cout << "Significado 2: " << actual->significado2 << endl;
            cout << "Significado 3: " << actual->significado3 << endl;

            int edit;
            cout << "Que significado desea editar? (1, 2 o 3): ";
            cin >> edit;

            cin.ignore();

            if (edit == 1)
            {
                cout << "Nuevo significado 1: ";
                getline(cin, actual->significado1);
            }
            else if (edit == 2)
            {
                cout << "Nuevo significado 2: ";
                getline(cin, actual->significado2);
            }
            else if (edit == 3)
            {
                cout << "Nuevo significado 3: ";
                getline(cin, actual->significado3);
            }
            else
            {
                cout << "Opcion invalida\n";
            }

            cout << "Palabra editada con exito\n";
            return;
        }
        actual = actual->siguiente;
    }
}


void eliminarpal(string buscar)
{
    diccionario* actual = inicio;

    while (actual != nullptr)
    {
        if (actual->palabra == buscar)
        {
            int eliminar;
            cout << "Seguro que desea eliminar esta palabra?\n";
            cout << "1. Si\n2. No\n";
            cin >> eliminar;

            if (eliminar == 1)
            {
                if (actual == inicio)
                {
                    inicio = actual->siguiente;
                    if (inicio != nullptr)
                        inicio->anterior = nullptr;
                }
                else
                {
                    actual->anterior->siguiente = actual->siguiente;

                    if (actual->siguiente != nullptr)
                        actual->siguiente->anterior = actual->anterior;
                }

                delete actual;
                cout << "Palabra eliminada con exito\n";
                return;
            }
            else
            {
                cout << "Operacion cancelada\n";
                return;
            }
        }

        actual = actual->siguiente;
    }
    cout << "La palabra no existe\n";
}

void impriizqui()
{
    diccionario* actual = inicio;

    while (actual != nullptr)
    {
            cout << "Palabra: " << actual->palabra << endl;
            cout << "Significado 1: " << actual->significado1 << endl;
            cout << "Significado 2: " << actual->significado2 << endl;
            cout << "Significado 3: " << actual->significado3 << endl;
            cout << "------------------------------\n" << actual->significado3 << endl;
        actual = actual->siguiente;
    }
}


void imprider()
{
    diccionario* actual = inicio;

    while (actual != nullptr && actual->siguiente != nullptr)
    {
        actual = actual->siguiente;
    }
    
    while (actual != nullptr)
    {
            cout << "Palabra: " << actual->palabra << endl;
            cout << "Significado 1: " << actual->significado1 << endl;
            cout << "Significado 2: " << actual->significado2 << endl;
            cout << "Significado 3: " << actual->significado3 << endl;
            cout << "------------------------------\n" << actual->significado3 << endl;
        actual = actual->anterior;
    }
}


void cocktailsort()
{
    if (inicio == nullptr) return;

    bool intercambio;
    diccionario* inicioLista = inicio;
    diccionario* fin = nullptr;

    do
    {
        intercambio = false;

        diccionario* actual = inicioLista;

        while (actual->siguiente != fin)
        {
            if (actual->palabra > actual->siguiente->palabra)
            {
                swap(actual->palabra, actual->siguiente->palabra);
                swap(actual->significado1, actual->siguiente->significado1);
                swap(actual->significado2, actual->siguiente->significado2);
                swap(actual->significado3, actual->siguiente->significado3);

                intercambio = true;
            }
            actual = actual->siguiente;
        }

        fin = actual;

        if (!intercambio) break;

        intercambio = false;

        while (actual->anterior != nullptr)
        {
            if (actual->anterior->palabra > actual->palabra)
            {
                swap(actual->palabra, actual->anterior->palabra);
                swap(actual->significado1, actual->anterior->significado1);
                swap(actual->significado2, actual->anterior->significado2);
                swap(actual->significado3, actual->anterior->significado3);

                intercambio = true;
            }
            actual = actual->anterior;
        }

        inicioLista = actual->siguiente;

    } while (intercambio);
}


void liberarMemoria()
{
    while (inicio != nullptr)
    {
        diccionario* temp = inicio;
        inicio = inicio->siguiente;
        delete temp;
    }
}


int main()
{
    int op;
    long cod;

    do
    {
        cout << "\nBienvenidos al Diccionario Personalizado\n";
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
            cout << "Palabra que se va adicionar: ";
            cin >> buscar;
                if (buscarpal(buscar))
                    cout << "La palabra ya existe\n";
                else
                    capturarpal(buscar);
                    cocktailsort();
                break;
            case 2:
            cout << "Palabra que va a consular: ";
            cin >> buscar;
                if (buscarpal(buscar))
                    {
                        imprimirpal(buscar);
                        cocktailsort();
                    }
                else
                    {
                        cout << "La palabra no existe\n";
                    }
                break;
            case 3:
            cout << "Palabra que se va editar: ";
            cin >> buscar;
                if (buscarpal(buscar))
                    {
                        editarpal(buscar);
                        cocktailsort();
                    }
                else
                    {
                        cout << "La palabra no existe\n";
                    }
                break;
            case 4:
            cout << "Palabra que se va eliminar: ";
            cin >> buscar;
                if (buscarpal(buscar))
                    {
                        eliminarpal(buscar);
                        cocktailsort();
                    }
                else
                    {
                        cout << "La palabra no existe\n";
                    }
                break;
            case 5:
                cocktailsort();
                impriizqui();
            break;
            case 6:
                cocktailsort();
                imprider();
            break;
            case 7:
                cout << "Gracias por usar el programa\n";
            break;
            default:
                cout << "Opcion invalida\n";
        }
    } while (op != 7);

    liberarMemoria();
    return 0;
}
