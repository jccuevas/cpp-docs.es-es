---
title: "Operador de sub&#237;ndice: | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "[]"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "operadores [C++], subíndice"
  - "operadores postfijos"
  - "[] (operador)"
  - "operador de subíndice, sintaxis"
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Operador de sub&#237;ndice:
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
postfix-expression [ expression ]  
```  
  
## Comentarios  
 Una expresión de postfijo \(que también puede ser una expresión primaria\) seguida del operador de subíndice, **\[ \]**, especifica la indexación de matrices.  
  
 Para obtener información sobre las matrices administradas, vea [Matrices](../windows/arrays-cpp-component-extensions.md).  
  
 Normalmente, el valor representado por *postfix\-expression* es un valor de puntero, como un identificador de matriz, y *expression* es un valor entero \(incluidos los tipos enumerados\).  Sin embargo, todo lo que se necesita desde el punto de vista sintáctico es que una de las expresiones sea de tipo puntero y que la otra sea de tipo entero.  Así pues, el valor entero podría estar en la posición de *postfix\-expression* y el valor de puntero podría estar en los corchetes de la posición de *expression* o subíndice.  Observe el fragmento de código siguiente:  
  
```  
int nArray[5] = { 0, 1, 2, 3, 4 };  
cout << nArray[2] << endl;            // prints "2"  
cout << 2[nArray] << endl;            // prints "2"  
```  
  
 En el ejemplo anterior, la expresión `nArray[2]` es idéntica a `2[nArray]`.  La razón es que el resultado de una expresión de subíndice *e1***\[** *e2* **\]** viene determinado por:  
  
 **\*\( \(** *e2* **\)** *\+* **\(***e1***\) \)**  
  
 La dirección producida por la expresión no es *e2* bytes desde la dirección *e1*.  En su lugar, la dirección se ha ampliado para producir el siguiente objeto en la matriz *e2*.  Por ejemplo:  
  
```  
double aDbl[2];  
```  
  
 Las direcciones de `aDb[0]` y `aDb[1]` están alejadas 8 bytes: el tamaño de un objeto de tipo **double**.  Esta ampliación según el tipo de objeto se realiza automáticamente en el lenguaje C\+\+ y se define en [Operadores de suma](../cpp/additive-operators-plus-and.md) donde se describe la suma y resta de operandos de tipo puntero.  
  
 Una expresión de subíndice también puede tener varios subíndices, como se indica a continuación:  
  
 *expression1* **\[***expression2***\] \[***expression3***\]**...  
  
 Las expresiones de subíndice se asocian de izquierda a derecha.  La expresión de subíndice del extremo izquierdo, *expression1***\[***expression2***\]**, se evalúa primero.  La dirección resultante de agregar *expression1* y *expression2* forma una expresión de puntero; entonces, se agrega *expression3* a esta expresión de puntero para formar una nueva expresión de puntero, y así sucesivamente, hasta que se haya agregado la última expresión de subíndice.  El operador de direccionamiento indirecto \(**\***\) se aplica después de que evalúe la última expresión de subíndice, a menos que el valor del puntero final apunte a un tipo de matriz.  
  
 Las expresiones con varios subíndices hacen referencia a elementos de matrices multidimensionales.  Una matriz multidimensional es una matriz cuyos elementos son matrices.  Por ejemplo, el primer elemento de una matriz tridimensional es una matriz con dos dimensiones.  En el ejemplo siguiente se declara y se inicializa una matriz bidimensional de caracteres simple:  
  
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
  
## Subíndices positivos y negativos  
 El primer elemento de una matriz es el elemento 0.  El intervalo de una matriz de C\+\+ es de *array*\[0\] a *array*\[*size* – 1\].  Sin embargo, C\+\+ admite subíndices positivos y negativos.  Los subíndices negativos deben situarse dentro de los límites de la matriz, ya que de lo contrario los resultados son impredecibles.  En el código siguiente se muestran subíndices de matriz positivos y negativos:  
  
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
  
 El subíndice negativo de la última línea puede generar un error en tiempo de ejecución porque señala una dirección 256 bytes más abajo en la memoria que el origen de la matriz.  El puntero `midArray` se inicializa en el centro de `intArray`, por lo que en él se pueden usar índices de matriz positivos y negativos.  Los errores de subíndice de matriz no generan errores en tiempo de compilación, pero producen resultados imprevisibles.  
  
 El operador de subíndice es conmutativo.  Por consiguiente, está garantizado que las expresiones *array*\[*index*\] y *array*\[*array*\] son equivalentes siempre que el operador subíndice no esté sobrecargado \(vea [Operadores sobrecargados](../cpp/operator-overloading.md)\).  La primera forma es la práctica más común de codificación, pero cualquiera de ellas funciona.  
  
## Vea también  
 [Expresiones postfijas](../cpp/postfix-expressions.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Matrices](../cpp/arrays-cpp.md)   
 [Matrices unidimensionales](../c-language/one-dimensional-arrays.md)   
 [Matrices multidimensionales](../c-language/multidimensional-arrays-c.md)