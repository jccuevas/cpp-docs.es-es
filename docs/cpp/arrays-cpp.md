---
title: Matrices (C++)
ms.date: 11/14/2019
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 91c57a9c4ef190dcace1813dd81739ac72e6b358
ms.sourcegitcommit: 217fac22604639ebd62d366a69e6071ad5b724ac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2019
ms.locfileid: "74188991"
---
# <a name="arrays-c"></a>Matrices (C++)

Una matriz es una secuencia de objetos del mismo tipo que ocupan un área de memoria contigua. Las matrices de estilo C tradicionales son el origen de muchos errores, pero siguen siendo comunes, especialmente en las bases de código anteriores. En moderno C++, recomendamos encarecidamente el uso de [STD:: Vector](../standard-library/vector-class.md) o [STD:: Array](../standard-library/array-class-stl.md) en lugar de las matrices de estilo C descritas en esta sección. Ambos tipos de biblioteca estándar almacenan sus elementos como un bloque de memoria contiguo, pero proporcionan mucha mayor seguridad de tipos junto con iteradores que se garantiza que señalan a una ubicación válida dentro de la secuencia. Para obtener más información, consulte [contenedores ( C++moderno)](containers-modern-cpp.md).

## <a name="stack-declarations"></a>Declaraciones de pila

En una C++ declaración de matriz, el tamaño de la matriz se especifica después del nombre de la variable, no después del nombre de tipo, como en otros lenguajes. En el ejemplo siguiente se declara una matriz de 1000 dobles para que se asigne en la pila. El número de elementos se debe proporcionar como un literal entero, o bien como una expresión constante, porque el compilador tiene que saber cuánto espacio de pila se va a asignar; no puede utilizar un valor calculado en tiempo de ejecución. A cada elemento de la matriz se le asigna un valor predeterminado de 0. Si no asigna un valor predeterminado, cada elemento contendrá inicialmente los valores aleatorios que se encuentren en esa ubicación.

```cpp
    constexpr size_t size = 1000;

    // Declare an array of doubles to be allocated on the stack
    double numbers[size] {0};

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i-1] * 1.1;
    }

    // Access each element
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }
```

El primer elemento de la matriz es el elemento 0 y el último elemento es el elemento (*n*-1), donde *n* es el número de elementos que puede contener la matriz. El número de elementos de la declaración debe ser de un tipo entero y debe ser mayor que 0. Es responsabilidad suya asegurarse de que el programa no pasa nunca un valor al operador de subíndice que sea mayor que `(size - 1)`.

Una matriz de tamaño cero solo es válida cuando la matriz es el último campo de una **estructura** o **Unión** y cuando se habilitan las extensiones de Microsoft (/ZE).

Las matrices basadas en la pila son más rápidas para asignar y acceder a las matrices basadas en montones, pero el número de elementos no puede ser tan grande que usa demasiada memoria de pila. La cantidad de tiempo depende del programa. Puede usar las herramientas de generación de perfiles para determinar si una matriz es demasiado grande.

## <a name="heap-declarations"></a>Declaraciones de montones

Si necesita una matriz demasiado grande para asignarla en la pila o cuyo tamaño no se puede conocer en tiempo de compilación, puede asignarla en el montón con una nueva expresión de [\[\]](new-operator-cpp.md) . El operador devuelve un puntero al primer elemento. Puede usar el operador de subíndice con la variable de puntero de la misma forma que con una matriz basada en la pila. También puede usar [aritmética de puntero](../c-language/pointer-arithmetic.md) para pasar el puntero a cualquier elemento arbitrario de la matriz. Es su responsabilidad asegurarse de que:

- siempre se conserva una copia de la dirección del puntero original para que se pueda eliminar la memoria cuando ya no se necesite la matriz.
- no incremente ni disminuya la dirección del puntero después de los límites de la matriz.

En el ejemplo siguiente se muestra cómo definir una matriz en el montón en tiempo de ejecución y cómo obtener acceso a los elementos de la matriz mediante el operador de subíndice o mediante aritmética de puntero:

```cpp

void do_something(size_t size)
{
    // Declare an array of doubles to be allocated on the heap
    double* numbers = new double[size]{ 0 };

    // Assign a new value to the first element
    numbers[0] = 1;

    // Assign a value to each subsequent element
    // (numbers[1] is the second element in the array.)
    for (size_t i = 1; i < size; i++)
    {
        numbers[i] = numbers[i - 1] * 1.1;
    }

    // Access each element with subscript operator
    for (size_t i = 0; i < size; i++)
    {
        std::cout << numbers[i] << " ";
    }

    // Access each element with pointer arithmetic
    // Use a copy of the pointer for iterating
    double* p = numbers;

    for (size_t i = 0; i < size; i++)
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    // Alternate method:
    // Reset p to numbers[0]:
    p = numbers;

    // Use address of pointer to compute bounds.
    // The compiler computes size as the number
    // of elements * (bytes per element).
    while (p < (numbers + size))
    {
        // Dereference the pointer, then increment it
        std::cout << *p++ << " ";
    }

    delete[] numbers; // don't forget to do this!

}
int main()
{
    do_something(108);
}

```

## <a name="initializing-arrays"></a>Inicializar matrices

Puede inicializar una matriz en un bucle, un elemento a la vez o en una única instrucción. El contenido de las dos matrices siguientes es idéntico:

```cpp
    int a[10];
    for (int i = 0; i < 10; ++i)
    {
        a[i] = i + 1;
    }

    int b[10]{ 1, 2, 3, 4, 5, 6, 7, 8, 9, 10 };
```

## <a name="passing-arrays-to-functions"></a>Pasar matrices a funciones

Cuando una matriz se pasa a una función, se pasa como un puntero al primer elemento. Esto es así tanto para las matrices basadas en pilas como para las basadas en montones. El puntero no contiene información de tamaño o tipo adicional. Este comportamiento se denomina *decadencia del puntero*. Al pasar una matriz a una función, siempre debe especificar el número de elementos en un parámetro independiente. Este comportamiento también implica que los elementos de la matriz no se copian cuando la matriz se pasa a una función. Para evitar que la función modifique los elementos, especifique el parámetro como un puntero a los elementos **const** .

En el ejemplo siguiente se muestra una función que acepta una matriz y una longitud. El puntero apunta a la matriz original, no a una copia. Dado que el parámetro no es **const**, la función puede modificar los elementos de la matriz.

```cpp
void process(double p*, const size_t len)
{
    std::cout << "process:\n";
    for (size_t i = 0; i < len; ++i)
    {
        // do something with p[i]
    }
}
```

Declare la matriz como const para que sea de solo lectura en el bloque de función:

```cpp
void process(const double p*, const size_t len);
```

También se puede declarar la misma función de estas maneras, sin ningún cambio de comportamiento. La matriz se sigue pasando como un puntero al primer elemento:

```cpp
// Unsized array
void process(const double p[] const size_t len);

// Fixed-size array. Length must still be specified explicitly.
void process(const double p[1000], const size_t len);
```

## <a name="multidimensional-arrays"></a>Matrices multidimensionales

Las matrices construidas a partir de otras matrices son matrices multidimensionales. Estas matrices multidimensionales se especifican colocando en orden varias expresiones constantes entre corchetes. Por ejemplo, considere esta declaración:

```cpp
int i2[5][7];
```

Especifica una matriz de tipo **int**, organizada conceptualmente en una matriz bidimensional de cinco filas y siete columnas, como se muestra en la ilustración siguiente:

![Diseño conceptual de una matriz&#45;multidimensional](../cpp/media/vc38rc1.gif "Diseño conceptual de una matriz&#45;multidimensional") <br/>
Diseño conceptual de una matriz multidimensional

En las declaraciones de matrices multidimensionales que tienen una lista de inicializadores (como se describe en [inicializadores](../cpp/initializers.md)), se puede omitir la expresión constante que especifica los límites de la primera dimensión. Por ejemplo:

```cpp
// arrays2.cpp
// compile with: /c
const int cMarkets = 4;
// Declare a float that represents the transportation costs.
double TransportCosts[][cMarkets] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};
```

La declaración anterior define una matriz de tres filas por cuatro columnas. Las filas representan fábricas y las columnas representan los mercados a los que distribuyen las fábricas. Los valores son los costos de transporte de las fábricas a los mercados. La primera dimensión de la matriz se omite, pero el compilador la completa examinando el inicializador.

El uso del operador de direccionamiento indirecto (*) en un tipo de matriz de n dimensiones produce una matriz n-1 dimensional. Si n es 1, el resultado es un valor escalar (o elemento de matriz).

Las matrices de C++ se almacenan por orden de fila principal. El orden de fila principal significa que el último subíndice es el que varía más rápidamente.

## <a name="example"></a>Ejemplo

La técnica para omitir la especificación de los límites de la primera dimensión de una matriz multidimensional se puede utilizar también en las declaraciones de función de la manera siguiente:

```cpp
// multidimensional_arrays.cpp
// compile with: /EHsc
// arguments: 3
#include <limits>   // Includes DBL_MAX
#include <iostream>

const int cMkts = 4, cFacts = 2;

// Declare a float that represents the transportation costs
double TransportCosts[][cMkts] = {
   { 32.19, 47.29, 31.99, 19.11 },
   { 11.29, 22.49, 33.47, 17.29 },
   { 41.97, 22.09,  9.76, 22.55 }
};

// Calculate size of unspecified dimension
const int cFactories = sizeof TransportCosts /
                  sizeof( double[cMkts] );

double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);

using namespace std;

int main( int argc, char *argv[] ) {
   double MinCost;

   if (argv[1] == 0) {
      cout << "You must specify the number of markets." << endl;
      exit(0);
   }
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);
   cout << "The minimum cost to Market " << argv[1] << " is: "
       << MinCost << "\n";
}

double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {
   double MinCost = DBL_MAX;

   for( size_t i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

La función `FindMinToMkt` se escribe de forma que para agregar nuevas fábricas no sea necesario modificar el código, solo volver a compilarlo.

## <a name="initializing-arrays"></a>Inicializar matrices

Si una clase tiene un constructor, las matrices de esa clase las inicializa un constructor. Si hay menos elementos en la lista de inicializadores que en la matriz, se usa el constructor predeterminado para los elementos restantes. Si no se define ningún constructor predeterminado para la clase, la lista de inicializadores debe estar completa (es decir, debe haber un inicializador para cada elemento de la matriz).

Considere la clase `Point`, que define dos constructores:

```cpp
// initializing_arrays1.cpp
class Point
{
public:
   Point()   // Default constructor.
   {
   }
   Point( int, int )   // Construct from two ints
   {
   }
};

// An array of Point objects can be declared as follows:
Point aPoint[3] = {
   Point( 3, 3 )     // Use int, int constructor.
};

int main()
{
}
```

El primer elemento de `aPoint` se construye utilizando el constructor `Point( int, int )`; los dos elementos restantes se crean con el constructor predeterminado.

Las matrices de miembros estáticos (ya sean **const** o not) se pueden inicializar en sus definiciones (fuera de la declaración de clase). Por ejemplo:

```cpp
// initializing_arrays2.cpp
class WindowColors
{
public:
    static const char *rgszWindowPartList[7];
};

const char *WindowColors::rgszWindowPartList[7] = {
    "Active Title Bar", "Inactive Title Bar", "Title Bar Text",
    "Menu Bar", "Menu Bar Text", "Window Background", "Frame"   };
int main()
{
}
```

## <a name="accessing-array-elements"></a>Obtener acceso a elementos de matriz

Se puede obtener acceso a los elementos individuales de una matriz mediante el operador de subíndice de matriz (`[ ]`). Si se utiliza una matriz unidimensional en una expresión que no tiene subíndice, el nombre de la matriz se evalúa como un puntero al primer elemento de la matriz.

```cpp
// using_arrays.cpp
int main() {
   char chArray[10];
   char *pch = chArray;   // Evaluates to a pointer to the first element.
   char   ch = chArray[0];   // Evaluates to the value of the first element.
   ch = chArray[3];   // Evaluates to the value of the fourth element.
}
```

Cuando se utilizan matrices multidimensionales, se pueden emplear varias combinaciones en las expresiones.

```cpp
// using_arrays_2.cpp
// compile with: /EHsc /W1
#include <iostream>
using namespace std;
int main() {
   double multi[4][4][3];   // Declare the array.
   double (*p2multi)[3];
   double (*p1multi);

   cout << multi[3][2][2] << "\n";   // C4700 Use three subscripts.
   p2multi = multi[3];               // Make p2multi point to
                                     // fourth "plane" of multi.
   p1multi = multi[3][2];            // Make p1multi point to
                                     // fourth plane, third row
                                     // of multi.
}
```

En el código anterior, `multi` es una matriz tridimensional de tipo **Double**. El puntero `p2multi` apunta a una matriz de tipo **Double** de tamaño tres. En este ejemplo, la matriz se utiliza con uno, dos y tres subíndices. Aunque es más frecuente especificar todos los subíndices, como en la instrucción `cout`, a veces es útil seleccionar un subconjunto concreto de elementos de la matriz, como se muestra en las instrucciones que hay después de `cout`.

## <a name="overloading-subscript-operator"></a>Sobrecargar el operador de subíndice

Al igual que otros operadores, el operador de subíndice (`[]`) puede ser redefinido por el usuario. El comportamiento predeterminado del operador de subíndice, si no está sobrecargado, consiste en combinar el nombre de la matriz y el subíndice usando el método siguiente:

`*((array_name) + (subscript))`

Como en toda suma que implica tipos de puntero, el ajuste de escala se realiza automáticamente para que se produzca el ajuste correspondiente al tamaño del tipo. Por lo tanto, el valor resultante no es *n* bytes del origen de array-Name; en su lugar, es el elemento *n*de la matriz. Para obtener más información sobre esta conversión, vea [operadores de adición](additive-operators-plus-and.md).

De igual forma, para las matrices multidimensionales, la dirección se deriva usando el método siguiente:

`((array_name) + (subscript1 * max2 * max3 * ... * maxn) + (subscript2 * max3 * ... * maxn) + ... + subscriptn))`

## <a name="arrays-in-expressions"></a>Matrices en expresiones

Cuando un identificador de un tipo de matriz aparece en una expresión distinta de `sizeof`, Address-of (`&`) o la inicialización de una referencia, se convierte en un puntero al primer elemento de la matriz. Por ejemplo:

```cpp
char szError1[] = "Error: Disk drive not ready.";
char *psz = szError1;
```

El puntero `psz` apunta al primer elemento de la matriz `szError1`. Las matrices, a diferencia de los punteros, no son valores l modificables. Por consiguiente, la siguiente asignación no es válida:

```cpp
szError1 = psz;
```

## <a name="see-also"></a>Vea también

[STD:: Array](../standard-library/array-class-stl.md)
