---
title: Matrices (C++) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring arrays, about declaring arrays
- multidimensional arrays
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: efd124254ece8f863afee13e132eea7945525a0e
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="arrays-c"></a>Matrices (C++)
Una matriz es una colección de objetos similares. El caso más simple de una matriz es un vector, que se puede declarar mediante la secuencia siguiente:  
  
```  
  
      decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1. El especificador de declaración:  
  
-   Un especificador de clase de almacenamiento opcional.  
  
-   Opcional **const** o `volatile` especificadores.  
  
-   El tipo de nombre de los elementos de la matriz.  
  
 2. El declarador:  
  
-   El identificador.  
  
-   Una expresión constante de tipo entero incluida entre corchetes, **[].** Si se declaran varias dimensiones con corchetes adicionales, se puede omitir la expresión constante en el primer conjunto de corchetes.  
  
-   Corchetes adicionales opcionales que encierran expresiones constantes.  
  
 3. Un inicializador opcional.  Vea [inicializadores](../cpp/initializers.md).  
  
 El número de elementos de la matriz viene determinado por la expresión constante. El primer elemento de la matriz es el elemento 0 y el último elemento es el (*n*-1) elemento, donde * n * es el número de elementos de la matriz puede contener. El *expresión constante* debe ser de un tipo entero y debe ser mayor que 0. Una matriz de tamaño cero es válida sólo cuando la matriz es el último campo en un `struct` o **union** y cuando están habilitadas las extensiones de Microsoft (/Ze).  
  
 En el ejemplo siguiente se muestra cómo definir una matriz en tiempo de ejecución:  
  
```  
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
  
 Las matrices son tipos derivados y, por tanto, pueden construirse a partir de cualquier otro tipo derivado o fundamental, salvo funciones, referencias y `void`.  
  
 Las matrices construidas a partir de otras matrices son matrices multidimensionales. Estas matrices multidimensionales se especifican colocando en orden varias expresiones constantes entre corchetes. Por ejemplo, considere esta declaración:  
  
```  
int i2[5][7];  
```  
  
 Especifica una matriz de tipo `int`, organizada conceptualmente en una matriz bidimensional de cinco filas y siete columnas, como se muestra en la ilustración siguiente:  
  
 ![Diseño conceptual de un múltiples &#45; matriz dimensional](../cpp/media/vc38rc1.gif "vc38RC1")  
Diseño conceptual de matriz multidimensional  
  
 En las declaraciones de matrices multidimensionales que tienen una lista de inicializadores (como se describe en [inicializadores](../cpp/initializers.md)), se puede omitir la expresión constante que especifica los límites de la primera dimensión. Por ejemplo:  
  
```  
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
  
-   [Uso de matrices](../cpp/using-arrays-cpp.md)  
  
-   [Matrices en expresiones](../cpp/arrays-in-expressions.md)  
  
-   [Interpretación del operador de subíndice](../cpp/interpretation-of-subscript-operator.md)  
  
-   [Direccionamiento indirecto en tipos de matriz](../cpp/indirection-on-array-types.md)  
  
-   [Orden de las matrices de C++](../cpp/ordering-of-cpp-arrays.md)  
  
## <a name="example"></a>Ejemplo  
 La técnica para omitir la especificación de los límites de la primera dimensión de una matriz multidimensional se puede utilizar también en las declaraciones de función de la manera siguiente:  
  
```  
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
  
## <a name="see-also"></a>Vea también  
 
