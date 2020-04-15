---
title: Punteros sin procesar (C++)
description: Cómo usar punteros sin procesar en C++
ms.date: 11/19/2019
helpviewer_keywords:
- pointers [C++]
ms.openlocfilehash: 919447fcab123ce6b838391d3cc295fb8a8fe95e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374674"
---
# <a name="raw-pointers-c"></a>Punteros sin procesar (C++)

Un puntero es un tipo de variable que almacena la dirección de un objeto en la memoria y se utiliza para tener acceso a ese objeto. Un *puntero sin formato* es un puntero cuya duración no está controlada por un objeto de encapsulación como un puntero [inteligente.](smart-pointers-modern-cpp.md) A un puntero sin formato se le puede asignar la dirección de otra variable que no sea de puntero, o se le puede asignar un valor de [nullptr](nullptr.md). Un puntero al que no se le ha asignado un valor contiene datos aleatorios.

También se puede *desreferenciar* un puntero para recuperar el valor del objeto al que apunta. El operador de *acceso miembro* proporciona acceso a los miembros de un objeto.

```cpp
    int* p = nullptr; // declare pointer and initialize it
                      // so that it doesn't store a random address
    int i = 5;
    p = &i; // assign pointer to address of object
    int j = *p; // dereference p to retrieve the value at its address

```

Un puntero puede apuntar a un objeto con tipo o a **void**. Cuando un programa asigna un nuevo objeto en el [montón](https://wikipedia.org/wiki/Heap) en memoria, recibe la dirección de ese objeto en forma de puntero. Estos punteros se denominan *punteros propietarios;* un puntero propietario (o una copia de él) debe utilizarse para eliminar explícitamente el objeto asignado al montón cuando ya no es necesario. Si no se elimina la memoria, se produce una pérdida de *memoria* y se hace que la ubicación de memoria no esté disponible para ningún otro programa del equipo. Para obtener más información, consulte [operadores nuevos y eliminados.](new-and-delete-operators.md)

```cpp

    MyClass* mc = new MyClass(); // allocate object on the heap
    mc->print(); // access class member
    delete mc; // delete object (please don't forget!)
```

Un puntero (si no se declara como **const**) se puede incrementar o disminuir para que apunte a una nueva ubicación en la memoria. Esto se denomina *aritmética* de puntero y se utiliza en la programación de estilo C para iterar elementos de matrices u otras estructuras de datos. No se puede hacer que un puntero **const** apunte a una ubicación de memoria diferente, y en ese sentido es muy similar a una [referencia.](references-cpp.md) Para obtener más información, consulte [const y punteros volátiles](const-and-volatile-pointers.md).

```cpp
    // declare a C-style string. Compiler adds terminating '\0'.
    const char* str = "Hello world";

    const int c = 1;
    const int* pconst = &c; // declare a non-const pointer to const int
    const int c2 = 2;
    pconst = &c2;  // OK pconst itself isn't const
    const int* const pconst2 = &c;
    // pconst2 = &c2; // Error! pconst2 is const.
```

En sistemas operativos de 64 bits, un puntero tiene un tamaño de 64 bits; el tamaño del puntero de un sistema determina la cantidad de memoria direccionable que puede tener. Todas las copias de un puntero apuntan a la misma ubicación de memoria. Los punteros (junto con las referencias) se utilizan ampliamente en C++ para pasar objetos más grandes a y desde funciones porque normalmente es mucho más eficaz copiar la dirección de 64 bits de un objeto que copiar un objeto completo. Al definir una función, especifique los parámetros de puntero como **const** a menos que desee que la función modifique el objeto. En general, las referencias **const** son la forma preferida de pasar objetos a funciones a menos que el valor del objeto pueda ser **nullptr**.

[Los punteros a funciones](#pointers_to_functions) permiten que las funciones se pasen a otras funciones y se utilizan para "callbacks" en la programación de estilo C. C++ moderno utiliza [expresiones lambda](lambda-expressions-in-cpp.md) para este propósito.

## <a name="initialization-and-member-access"></a>Inicialización y acceso a miembros

En el ejemplo siguiente se muestra cómo declarar un puntero sin formato e inicializarlo con un objeto asignado en el montón y, a continuación, cómo usarlo. También muestra algunos de los peligros asociados con los punteros crudos. (Recuerde, esto es programación de estilo C y no moderno C ++!)

```cpp
#include <iostream>
#include <string>

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

// Accepts a MyClass pointer
void func_A(MyClass* mc)
{
    // Modify the object that mc points to.
    // All copies of the pointer will point to
    // the same modified object.
    mc->num = 3;
}

// Accepts a MyClass object
void func_B(MyClass mc)
{
    // mc here is a regular object, not a pointer.
    // Use the "." operator to access members.
    // This statement modifies only the local copy of mc.
    mc.num = 21;
    std::cout << "Local copy of mc:";
    mc.print(); // "Erika, 21"
}


int main()
{
    // Use the * operator to declare a pointer type
    // Use new to allocate and initialize memory
    MyClass* pmc = new MyClass{ 108, "Nick" };

    // Prints the memory address. Usually not what you want.
    std:: cout << pmc << std::endl;

    // Copy the pointed-to object by dereferencing the pointer
    // to access the contents of the memory location.
    // mc is a separate object, allocated here on the stack
    MyClass mc = *pmc;

    // Declare a pointer that points to mc using the addressof operator
    MyClass* pcopy = &mc;

    // Use the -> operator to access the object's public members
    pmc->print(); // "Nick, 108"

    // Copy the pointer. Now pmc and pmc2 point to same object!
    MyClass* pmc2 = pmc;

    // Use copied pointer to modify the original object
    pmc2->name = "Erika";
    pmc->print(); // "Erika, 108"
    pmc2->print(); // "Erika, 108"

    // Pass the pointer to a function.
    func_A(mc);
    pmc->print(); // "Erika, 3"
    pmc2->print(); // "Erika, 3"

    // Dereference the pointer and pass a copy
    // of the pointed-to object to a function
    func_B(*mc);
    pmc->print(); // "Erika, 3" (original not modified by function)

    delete(pmc); // don't forget to give memory back to operating system!
   // delete(pmc2); //crash! memory location was already deleted
}
```

## <a name="pointer-arithmetic-and-arrays"></a>Aritmética de puntero y matrices

Los punteros y matrices están estrechamente relacionados. Cuando se pasa una matriz por valor a una función, se pasa como un puntero al primer elemento. En el ejemplo siguiente se muestran las siguientes propiedades importantes de punteros y matrices:

- el `sizeof` operador devuelve el tamaño total en bytes de una matriz
- para determinar el número de elementos, divida los bytes totales por el tamaño de un elemento
- cuando una matriz se pasa a una función, *se descompone* a un tipo de puntero
- el `sizeof` operador cuando se aplica a un puntero devuelve el tamaño del puntero, 4 bytes en x86 u 8 bytes en x64

```cpp
#include <iostream>

void func(int arr[], int length)
{
    // returns pointer size. not useful here.
    size_t test = sizeof(arr);

    for(int i = 0; i < length; ++i)
    {
        std::cout << arr[i] << " ";
    }
}

int main()
{

    int i[5]{ 1,2,3,4,5 };
    // sizeof(i) = total bytes
    int j = sizeof(i) / sizeof(i[0]);
    func(i,j);
}
```

Ciertas operaciones aritméticas se pueden realizar en punteros no contrast para que apunten a una nueva ubicación de memoria. Un puntero se puede incrementar y disminuir **++** **+=** mediante **-=** **--** los operadores , , y . Esta técnica se puede utilizar en matrices y es especialmente útil en búferes de datos sin tipo. Un **\* vacío** aumenta por el tamaño de un **char** (1 byte). Un puntero con tipo aumenta por el tamaño del tipo al que apunta.

En el ejemplo siguiente se muestra cómo se puede utilizar la aritmética de punteros para tener acceso a píxeles individuales en un mapa de bits en Windows. Tenga en cuenta el uso de **new** y **delete**y el operador de desreferencia.

```cpp
#include <Windows.h>
#include <fstream>

using namespace std;

int main()
{

    BITMAPINFOHEADER header;
    header.biHeight = 100; // Multiple of 4 for simplicity.
    header.biWidth = 100;
    header.biBitCount = 24;
    header.biPlanes = 1;
    header.biCompression = BI_RGB;
    header.biSize = sizeof(BITMAPINFOHEADER);

    constexpr int bufferSize = 30000;
    unsigned char* buffer = new unsigned char[bufferSize];

    BITMAPFILEHEADER bf;
    bf.bfType = 0x4D42;
    bf.bfSize = header.biSize + 14 + bufferSize;
    bf.bfReserved1 = 0;
    bf.bfReserved2 = 0;
    bf.bfOffBits = sizeof(BITMAPFILEHEADER) + sizeof(BITMAPINFOHEADER); //54

    // Create a gray square with a 2-pixel wide outline.
    unsigned char* begin = &buffer[0];
    unsigned char* end = &buffer[0] + bufferSize;
    unsigned char* p = begin;
    constexpr int pixelWidth = 3;
    constexpr int borderWidth = 2;

    while (p < end)
    {
            // Is top or bottom edge?
        if ((p < begin + header.biWidth * pixelWidth * borderWidth)
            || (p > end - header.biWidth * pixelWidth * borderWidth)
            // Is left or right edge?
            || (p - begin) % (header.biWidth * pixelWidth) < (borderWidth * pixelWidth)
            || (p - begin) % (header.biWidth * pixelWidth) > ((header.biWidth - borderWidth) * pixelWidth))
        {
            *p = 0x0; // Black
        }
        else
        {
            *p = 0xC3; // Gray
        }
        p++; // Increment one byte sizeof(unsigned char).
    }

    ofstream wf(R"(box.bmp)", ios::out | ios::binary);

    wf.write(reinterpret_cast<char*>(&bf), sizeof(bf));
    wf.write(reinterpret_cast<char*>(&header), sizeof(header));
    wf.write(reinterpret_cast<char*>(begin), bufferSize);

    delete[] buffer; // Return memory to the OS.
    wf.close();
}
```

## <a name="void-pointers"></a>punteros void*

Un puntero a **void** simplemente apunta a una ubicación de memoria sin procesar. A veces es necesario utilizar punteros **void,\* ** por ejemplo, al pasar entre el código C+ + y las funciones C.

Cuando un puntero con tipo se convierte en un puntero void, el contenido de la ubicación de memoria no cambia, pero se pierde la información de tipo, por lo que no se pueden realizar operaciones de incremento o disminución. Una ubicación de memoria se puede convertir, por ejemplo, de MyClass* a void* y volver a MyClass*. Estas operaciones son intrínsecamente propensas a errores y requieren un gran cuidado para evitar errores. Modern C++ desaconseja el uso de punteros void a menos que sea absolutamente necesario.

```cpp

//func.c
void func(void* data, int length)
{
    char* c = (char*)(data);

    // fill in the buffer with data
    for (int i = 0; i < length; ++i)
    {
        *c = 0x41;
        ++c;
    }
}

// main.cpp
#include <iostream>

extern "C"
{
    void func(void* data, int length);
}

class MyClass
{
public:
    int num;
    std::string name;
    void print() { std::cout << name << ":" << num << std::endl; }
};

int main()
{
    MyClass* mc = new MyClass{10, "Marian"};
    void* p = static_cast<void*>(mc);
    MyClass* mc2 = static_cast<MyClass*>(p);
    std::cout << mc2->name << std::endl; // "Marian"

    // use operator new to allocate untyped memory block
    void* pvoid = operator new(1000);
    char* pchar = static_cast<char*>(pvoid);
    for(char* c = pchar; c < pchar + 1000; ++c)
    {
        *c = 0x00;
    }
    func(pvoid, 1000);
    char ch = static_cast<char*>(pvoid)[0];
    std::cout << ch << std::endl; // 'A'
    operator delete(p);
}
```

## <a name="pointers-to-functions"></a><a name="pointers_to_functions"></a>Punteros a funciones

En la programación de estilo C, los punteros de función se utilizan principalmente para pasar funciones a otras funciones. En este escenario, el autor de la llamada puede personalizar el comportamiento de una función sin modificarla. En C+++ moderno, las [expresiones lambda](lambda-expressions-in-cpp.md) proporcionan la misma capacidad con mayor seguridad de tipos y otras ventajas.

Una declaración de puntero de función especifica la firma que debe tener la función señalada:

```cpp
// Declare pointer to any function that...

// ...accepts a string and returns a string
string (*g)(string a);

// has no return value and no parameters
void (*x)();

// ...returns an int and takes three parameters
// of the specified types
int (*i)(int i, string s, double d);
```

En el ejemplo `combine` siguiente se muestra una función `std::string` que toma `std::string`como parámetro cualquier función que acepte a y devuelve un archivo . Dependiendo de la función `combine` que se le pasa antepondrá o anexará una cadena.

```cpp
#include <iostream>
#include <string>

using namespace std;

string base {"hello world"};

string append(string s)
{
    return base.append(" ").append(s);
}

string prepend(string s)
{
    return s.append(" ").append(base);
}

string combine(string s, string(*g)(string a))
{
    return (*g)(s);
}

int main()
{
    cout << combine("from MSVC", append) << "\n";
    cout << combine("Good morning and", prepend) << "\n";
}
```

## <a name="see-also"></a>Consulte también

[Operador](smart-pointers-modern-cpp.md)
de direccionamiento indirecto de punteros[inteligentes: *](indirection-operator-star.md)<br/>
[address-of (Operador): &](address-of-operator-amp.md)</br>
[Bienvenido de nuevo a C++](welcome-back-to-cpp-modern-cpp.md)
