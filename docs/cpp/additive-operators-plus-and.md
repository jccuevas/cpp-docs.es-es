---
title: "Operadores de adici&#243;n: + y - | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "-"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "- (operador), operador de adición en C++"
  - "+ (operador), operadores de adición"
  - "operadores de adición"
  - "operadores aritméticos [C++], operadores de adición"
  - "operadores [C++], suma"
  - "operador de resta, operadores de adición"
ms.assetid: d4afafe7-e201-4c69-a649-37f17756e784
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de adici&#243;n: + y -
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
expression + expression   
expression – expression  
```  
  
## Comentarios  
 Los operadores aditivos son:  
  
-   Suma \(**\+**\)  
  
-   Resta \(**–**\)  
  
 Estos operadores binarios tienen asociatividad de izquierda a derecha.  
  
 Los operadores aditivos toman operandos de tipos aritméticos o de puntero.  El resultado del operador de suma \(**\+**\) es la suma de los operandos.  El resultado del operador de resta \(**–**\) es la diferencia entre los operandos.  Si uno o ambos operandos son punteros, deben ser punteros a objetos, no a funciones.  Si ambos operandos son punteros, los resultados no son significativos a menos que ambos sean punteros a objetos de la misma matriz.  
  
 Los operadores aditivos toman operandos de tipos *aritméticos*, *enteros* y *escalares*.  Se definen en la tabla siguiente.  
  
### Tipos utilizados con operadores de suma  
  
|Tipo|Significado|  
|----------|-----------------|  
|*aritméticos*|Los tipos enteros y de punto flotante se denominan colectivamente tipos “aritméticos”.|  
|*enteros*|Los tipos char e int de todos los tamaños \(long, short\) y las enumeraciones son tipos “enteros”.|  
|*escalares*|Los operandos escalares son operandos de tipo aritmético o puntero.|  
  
 Las combinaciones válidas para estos operadores son:  
  
 *aritmético* \+ *aritmético*  
  
 *escalar* \+ *entero*  
  
 *entero* \+ *escalar*  
  
 *aritmético* – *aritmético*  
  
 *escalar* – *escalar*  
  
 Tenga en cuenta que la suma y resta no son operaciones equivalentes.  
  
 Si ambos operandos son de tipo aritmético, las conversiones descritas en [Conversiones aritméticas](../misc/arithmetic-conversions.md) se aplican a los operandos y el resultado es de tipo convertido.  
  
## Ejemplo  
  
```  
// expre_Additive_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
#define SIZE 5  
using namespace std;  
int main() {  
   int i = 5, j = 10;  
   int n[SIZE] = { 0, 1, 2, 3, 4 };  
   cout  << "5 + 10 = " << i + j << endl  
         << "5 - 10 = " << i - j << endl;  
  
   // use pointer arithmetic on array  
  
   cout << "n[3] = " << *( n + 3 ) << endl;  
}  
```  
  
## Adición de puntero  
 Si uno de los operandos de una operación de suma es un puntero a una matriz de objetos, el otro debe ser de tipo entero.  El resultado es un puntero del mismo tipo que el puntero original y que apunta a otro elemento de la matriz.  En el siguiente fragmento de código se muestra este concepto:  
  
```  
short IntArray[10]; // Objects of type short occupy 2 bytes  
short *pIntArray = IntArray;  
  
for( int i = 0; i < 10; ++i )  
{  
    *pIntArray = i;  
    cout << *pIntArray << "\n";  
    pIntArray = pIntArray + 1;  
}  
```  
  
 Aunque el valor entero 1 se suma a `pIntArray`, eso no significa “sumar 1 a la dirección”, sino más bien "ajustar el puntero para que apunte al siguiente objeto de la matriz”, que resulta estar alejado 2 bytes \(o `sizeof( int )`\).  
  
> [!NOTE]
>  El código con la forma `pIntArray = pIntArray + 1` raramente aparece en programas de C\+\+; para realizar un incremento, son preferibles estas formas: `pIntArray++` o `pIntArray += 1`.  
  
## Resta de puntero  
 Si ambos operandos son punteros, el resultado de la resta es la diferencia \(en elementos de matriz\) entre los operandos.  La expresión de resta produce un resultado entero con signo de tipo ptrdiff\_t \(definido en el archivo de inclusión estándar STDDEF.H\).  
  
 Uno de los operandos puede ser de tipo entero, siempre y cuando sea el segundo operando.  El resultado de la resta es del mismo tipo que el puntero original.  El valor de la resta es un puntero al elemento de la matriz \(*n* – *i*\), donde *n* es el elemento al que señala el puntero original e *i* es el valor entero del segundo operando.  
  
## Vea también  
 [Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Suma de tipos de puntero](../misc/addition-of-pointer-types.md)   
 [Sustracción de tipos de puntero](../misc/subtraction-of-pointer-types.md)   
 [Operadores de adición de C](../c-language/c-additive-operators.md)