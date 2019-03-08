---
title: Matrices (C++)
ms.date: 11/19/2018
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
ms.openlocfilehash: 176e358bd0217ac914eb4ee6079126d3f429b6dd
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52176884"
---
# <a name="arrays-c"></a>Matrices (C++)

Una matriz es una colección de objetos similares. El caso más simple de una matriz es un vector, que se puede declarar mediante la secuencia siguiente:

> *decl-specifier* *identificador* **\[** *expresión-constante* **]**<br/>
> *decl-specifier* *identificador*  **\[]**<br/>
> *decl-specifier* *identificador* **\[]\[** *expresión-constante* **]** . . .<br/>
> *decl-specifier* *identificador* **\[** *expresión-constante* **]** **\[** *expresión-constante* **]** . . .

1. El especificador de declaración:

   - Un especificador de clase de almacenamiento opcional.

   - Opcional **const** o **volátil** especificadores.

   - El tipo de nombre de los elementos de la matriz.

1. El declarador:

   - El identificador.

   - Una expresión constante de tipo entero incluida entre corchetes,  **\[]**. Si se declaran varias dimensiones con corchetes adicionales, se puede omitir la expresión constante en el primer conjunto de corchetes.

   - Corchetes adicionales opcionales que encierran expresiones constantes.

1. Un inicializador opcional. Para obtener más información, consulte [inicializadores](../cpp/initializers.md).

El número de elementos de la matriz viene dado por la *expresión-constante*. El primer elemento de la matriz es el elemento 0 y el último elemento es el (*n*-1) el elemento, donde *n* es el número de elementos que puede contener la matriz. El *expresión-constante* debe ser de tipo entero y debe ser mayor que 0. Una matriz de tamaño cero es válida únicamente cuando la matriz es el último campo de un **struct** o **unión** y cuando las extensiones de Microsoft (/Ze) están habilitadas.

En el ejemplo siguiente se muestra cómo definir una matriz en tiempo de ejecución:

```cpp
// arrays.cpp
// compile with: /EHsc
#include <iostream>

int main() {
   using namespace std;
   int size = 3, i = 0;

   int* myarr = new int[size];

   for (i = 0 ; i < size ; i++)
      myarr[i] = 10;

   for (i = 0 ; i < size ; i++)
      printf_s("myarr[%d] = %d\n", i, myarr[i]);

   delete [] myarr;
}
```

Las matrices son tipos derivados y, por tanto, se puede construir de cualquier otro tipo derivado o fundamental, salvo funciones, referencias y **void**.

Las matrices construidas a partir de otras matrices son matrices multidimensionales. Estas matrices multidimensionales se especifican colocando en orden varias expresiones constantes entre corchetes. Por ejemplo, considere esta declaración:

```cpp
int i2[5][7];
```

Especifica una matriz de tipo **int**, organizada conceptualmente en una matriz bidimensional de cinco filas y siete columnas, como se muestra en la ilustración siguiente:

![Diseño conceptual de un varios&#45;una matriz unidimensional](../cpp/media/vc38rc1.gif "diseño Conceptual de un varios&#45;una matriz unidimensional") <br/>
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

Temas de esta sección:

- [Uso de matrices](../cpp/using-arrays-cpp.md)

- [Matrices en expresiones](../cpp/arrays-in-expressions.md)

- [Interpretación del operador de subíndice](../cpp/interpretation-of-subscript-operator.md)

- [Direccionamiento indirecto en tipos de matriz](../cpp/indirection-on-array-types.md)

- [Orden de las matrices de C++](../cpp/ordering-of-cpp-arrays.md)

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

   for( int i = 0; i < cFacts; ++i )
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?
         MinCost : TransportCosts[i][Mkt];

   return MinCost;
}
```

```Output
The minimum cost to Market 3 is: 17.29
```

## <a name="comments"></a>Comentarios

La función `FindMinToMkt` se escribe de forma que para agregar nuevas fábricas no sea necesario modificar el código, solo volver a compilarlo.
