---
title: "Operador de subíndice: | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '[]'
dev_langs:
- C++
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1fbcb3657af276cdfc9aa05d461c090b76f6de0b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="subscript-operator"></a>Operador de subíndice:
## <a name="syntax"></a>Sintaxis  
  
```  
  
postfix-expression [ expression ]  
```  
  
## <a name="remarks"></a>Comentarios  
 Una expresión de postfijo (que también se puede ser una expresión primaria) seguida del operador de subíndice, **[]**, especifica la indización de matrices.  
  
 Para obtener información sobre las matrices administradas, vea [matrices](../windows/arrays-cpp-component-extensions.md).  
  
 Normalmente, el valor representado por *postfix-expression* es un valor de puntero, como un identificador de matriz, y *expresión* es un valor entero (incluidos los tipos enumerados). Sin embargo, todo lo que se necesita desde el punto de vista sintáctico es que una de las expresiones sea de tipo puntero y que la otra sea de tipo entero. Por tanto, el valor entero podría estar en el *postfix-expression* posición y el valor de puntero pudieron estar en las llaves de la *expresión* o la posición de subíndice. Observe el fragmento de código siguiente:  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 En el ejemplo anterior, la expresión `nArray[2]` es idéntica a `2[nArray]`. El motivo es que el resultado de una expresión de subíndice *e1***[** *e2* **]** viene dado por:  
  
 **\*((** *e2* **)**  *+*  **(***e1***))**  
  
 La dirección producida por la expresión no es *e2* bytes a partir de la dirección *e1*. En su lugar, la dirección se ha ampliado para producir el siguiente objeto de la matriz *e2*. Por ejemplo:  
  
```  
double aDbl[2];  
```  
  
 Las direcciones de `aDb[0]` y `aDb[1]` están alejadas 8 bytes, el tamaño de un objeto de tipo **doble**. Esta ampliación según el tipo de objeto se realiza automáticamente en el lenguaje C++ y se define en [operadores de suma](../cpp/additive-operators-plus-and.md) donde se describe la suma y resta de operandos de tipo de puntero.  
  
 Una expresión de subíndice también puede tener varios subíndices, como se indica a continuación:  
  
 *expression1* **[***expression2***] [***expression3***]**...  
  
 Las expresiones de subíndice se asocian de izquierda a derecha. La expresión de subíndice del extremo izquierdo, *expression1***[***expression2***]**, se evalúa primero. La dirección resultante de agregar *expression1* y *expression2* forma una expresión de puntero; entonces, se agrega *expression3* a esta expresión de puntero para formar una nueva expresión de puntero, y así sucesivamente, hasta que se haya agregado la última expresión de subíndice. El operador de direccionamiento indirecto (**\***) se aplica después de la última expresión de subíndice se evalúa, a menos que el valor del puntero final apunta un tipo de matriz.  
  
 Las expresiones con varios subíndices hacen referencia a elementos de matrices multidimensionales. Una matriz multidimensional es una matriz cuyos elementos son matrices. Por ejemplo, el primer elemento de una matriz tridimensional es una matriz con dos dimensiones. En el ejemplo siguiente se declara y se inicializa una matriz bidimensional de caracteres simple:  
  
```  
// expre_Subscript_Operator.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
#define MAX_ROWS 2  
#define MAX_COLS 2  
  
int main() {  
   char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };  
   for ( int i = 0; i < MAX_ROWS; i++ )  
      for ( int j = 0; j < MAX_COLS; j++ )  
         cout << c[ i ][ j ] << endl;  
}  
```  
  
## <a name="positive-and-negative-subscripts"></a>Subíndices positivos y negativos  
 El primer elemento de una matriz es el elemento 0. El rango de una matriz de C++ es de *matriz*[0] a *matriz*[*tamaño* - 1]. Sin embargo, C++ admite subíndices positivos y negativos. Los subíndices negativos deben situarse dentro de los límites de la matriz, ya que de lo contrario los resultados son impredecibles. En el código siguiente se muestran subíndices de matriz positivos y negativos:  
  
```  
#include <iostream>  
using namespace std;  
  
int main() {  
    int intArray[1024];  
    for (int i = 0, j = 0; i < 1024; i++)  
    {  
        intArray[i] = j++;  
    }  
  
    cout << intArray[512] << endl;// 512  
  
    int *midArray = &intArray[512];  // pointer to the middle of the array  
  
    cout << midArray[-256] << endl;   // 256  
  
    cout << intArray[-256] << endl; // unpredictable  
}  
```  
  
 El subíndice negativo de la última línea puede generar un error en tiempo de ejecución porque señala una dirección 256 bytes más abajo en la memoria que el origen de la matriz. El puntero `midArray` se inicializa en el centro de `intArray`, por lo que en él se pueden usar índices de matriz positivos y negativos. Los errores de subíndice de matriz no generan errores en tiempo de compilación, pero producen resultados imprevisibles.  
  
 El operador de subíndice es conmutativo. Por lo tanto, las expresiones *matriz*[*índice*] y *matriz*[*matriz*] se garantiza que sean equivalentes siempre que el subíndice no se sobrecarga el operador (vea [operadores sobrecargados](../cpp/operator-overloading.md)). La primera forma es la práctica más común de codificación, pero cualquiera de ellas funciona.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones de postfijo](../cpp/postfix-expressions.md)   
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Arrays](../cpp/arrays-cpp.md)  (Matrices)  
 [Matrices unidimensionales](../c-language/one-dimensional-arrays.md)   
 [Matrices multidimensionales](../c-language/multidimensional-arrays-c.md)