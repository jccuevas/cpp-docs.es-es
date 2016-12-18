---
title: "Operadores de multiplicaci&#243;n y el operador de m&#243;dulo | Microsoft Docs"
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
  - "%"
  - "/"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "% (operador)"
  - "* (operador)"
  - "operadores aritméticos [C++], operadores de multiplicación"
  - "operador de división"
  - "operador de división, operadores de multiplicación"
  - "operador de módulo, C+"
  - "operador de multiplicación [C++], operadores de multiplicación"
  - "operadores de multiplicación [C++]"
  - "operadores [C++], multiplicativo"
ms.assetid: b53ea5da-d0b4-40dc-98f3-0aa52d548293
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operadores de multiplicaci&#243;n y el operador de m&#243;dulo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
expression * expression   
expression / expression   
expression % expression  
```  
  
## Comentarios  
 Los operadores multiplicativos son:  
  
-   Multiplicación \(**\***\)  
  
-   División \(**\/**\)  
  
-   Módulo \(resto de la división\) \(`%`\)  
  
 Estos operadores binarios tienen asociatividad de izquierda a derecha.  
  
 Los operadores multiplicativos toman operandos de tipos aritméticos.  El operador de módulo \(`%`\) tiene un requisito más estricto en tanto que sus operandos deben ser de tipo entero. \(Para obtener el resto de una división de coma flotante, utilice la función de tiempo de ejecución, [fmod](../c-runtime-library/reference/fmod-fmodf.md)\). Las conversiones descritas en [Conversiones aritméticas](../misc/arithmetic-conversions.md) se aplican a los operandos y el resultado es del tipo convertido.  
  
 El operador de multiplicación produce el resultado de multiplicar el primer operando por el segundo.  
  
 El operador de división produce el resultado de dividir el primer operando por el segundo.  
  
 El operador de módulo produce el resto proporcionado por la expresión siguiente, donde *e1* es el primer operando y *e2* es el segundo: *e1* – \(*e1* y *e2*\) \* *e2*, donde ambos operandos son de tipos enteros.  
  
 La división por 0 en una expresión de división o de módulo es indefinida y provoca un error en tiempo de ejecución.  Por consiguiente, las expresiones siguientes generan resultados erróneos, indefinidos:  
  
```  
i % 0  
f / 0.0  
```  
  
 Si ambos operandos de una multiplicación, una división o una expresión de módulo tienen el mismo signo, el resultado es positivo.  De lo contrario, el resultado es negativo.  El resultado del signo de una operación de módulo lo define la implementación.  
  
> [!NOTE]
>  Como las conversiones realizadas por los operadores multiplicativos no proporcionan condiciones de desbordamiento o subdesbordamiento, la información puede perderse si el resultado de una operación multiplicativa no se puede representar en el tipo de los operandos después de la conversión.  
  
## Específicos de Microsoft  
 En Microsoft C\+\+, el resultado de una expresión de módulo tiene siempre el mismo signo que el primer operando.  
  
## FIN de Específicos de Microsoft  
 Si la división calculada de dos enteros es inexacta y solo un operando es negativo, el resultado es el entero mayor \(en magnitud, independientemente del signo\) que es menor que el valor exacto que produciría la operación de división.  Por ejemplo, el valor calculado de –11 \/ 3 es –3,666666666.  El resultado de esa división entera es –3.  
  
 La relación entre los operadores multiplicativos está determinada por la identidad \(*e1* \/ *e2*\) \* *e2* \+ *e1* % *e2* \=\= *e1*.  
  
## Ejemplo  
 El siguiente programa muestra los operadores multiplicativos.  Observe que ambos operandos de `10 / 3` se deben convertir explícitamente al tipo `float` para evitar el truncamiento, de manera que los dos operandos son de tipo `float` antes de la división.  
  
```  
// expre_Multiplicative_Operators.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   int x = 3, y = 6, z = 10;  
   cout  << "3 * 6 is " << x * y << endl  
         << "6 / 3 is " << y / x << endl  
         << "10 % 3 is " << z % x << endl  
         << "10 / 3 is " << (float) z / x << endl;  
}  
```  
  
## Vea también  
 [Expresiones con operadores binarios](../cpp/expressions-with-binary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Operadores de multiplicación de C](../c-language/c-multiplicative-operators.md)