---
title: "Semántica de las expresiones | Documentos de Microsoft"
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
- grammar, expressions
- expressions [C++], semantics
- expression evaluation
- expression evaluation, about expression evaluation
ms.assetid: 4a792154-533b-48b9-8709-31bfc170f0a7
caps.latest.revision: 7
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
ms.openlocfilehash: 09b65ee050e856c4dcecba269c46a08c8d2d7fb5
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="semantics-of-expressions"></a>Semántica de las expresiones
Las expresiones se evalúan según la prioridad y agrupación de sus operadores. ([Prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md) en [convenciones léxicas](../cpp/lexical-conventions.md), muestra las relaciones de C++ imponen operadores en expresiones.)  
  
## <a name="order-of-evaluation"></a>Orden de evaluación  
 Considere este ejemplo:  
  
```cpp  
// Order_of_Evaluation.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main()  
{  
    int a = 2, b = 4, c = 9;  
  
    cout << a + b * c << "\n";  
    cout << a + (b * c) << "\n";  
    cout << (a + b) * c << "\n";  
}  
```  
  
```Output  
38  
38  
54  
```  
  
 ![Orden de evaluación en una expresión](../cpp/media/vc38zv1.gif "vc38ZV1")  
Orden de expresión-evaluación  
  
 El orden en que se evalúa la expresión mostrada en la ilustración anterior viene determinado por la prioridad y la asociatividad de los operadores:  
  
1.  La multiplicación (*) tiene la prioridad más alta en esta expresión; por consiguiente, la subexpresión `b * c` se evalúa primero.  
  
2.  La suma (+) es la siguiente operación con mayor prioridad, por lo que `a` se suma al producto de `b` y `c`.  
  
3.  El desplazamiento a la izquierda (<<) tiene la prioridad más baja en la expresión, pero aparece dos veces. Como el operador de desplazamiento a la izquierda se agrupa de izquierda a derecha, la subexpresión de la izquierda se evalúa primero y después se evalúa la de la derecha.  
  
 Cuando se utilizan paréntesis para agrupar subexpresiones, se modifica la prioridad, así como el orden en que se evalúa la expresión, como se muestra en la ilustración siguiente.  
  
 ![Orden de evaluación de expresión con paréntesis](../cpp/media/vc38zv2.gif "vc38ZV2")  
Orden de expresión-evaluación con paréntesis  
  
 Las expresiones como las de la ilustración anterior se evalúan simplemente para que se apliquen sus efectos secundarios (en este caso, para transferir información al dispositivo de salida estándar).  
  
## <a name="notation-in-expressions"></a>Notación en expresiones  
 El lenguaje C++ indica ciertas compatibilidades al especificar operandos. En la tabla siguiente se muestra los tipos de operandos aceptables para los operadores que requieren operandos de tipo *tipo*.  
  
### <a name="operand-types-acceptable-to-operators"></a>Tipos de operando aceptables para los operadores  
  
|Tipo esperado|Tipos permitidos|  
|-------------------|-------------------|  
|*type*|`const`*tipo*<br /> `volatile`*tipo*<br /> *tipo de*&<br /> `const`*tipo*&<br /> `volatile`*tipo*&<br /> `volatile const`*tipo*<br /> `volatile const`*tipo*&|  
|*tipo de*\*|*tipo de*\*<br /> `const`*tipo*\*<br /> `volatile`*tipo*\*<br /> `volatile const`*tipo*\*|  
|`const`*tipo*|*type*<br /> `const`*tipo*<br />`const`*tipo*&|  
|`volatile`*tipo*|*type*<br /> `volatile`*tipo*<br /> `volatile`*tipo*&|  
  
 Dado que las reglas anteriores se pueden utilizar combinadas, se puede proporcionar un puntero const a un objeto volatile cuando se espera un puntero.  
  
## <a name="ambiguous-expressions"></a>Expresiones ambiguas  
 Algunas expresiones son ambiguas en su significado. Estas expresiones aparecen frecuentemente cuando el valor de un objeto se modifica más de una vez en la misma expresión. Estas expresiones se basan en un orden concreto de evaluación donde el lenguaje no define uno. Considere el ejemplo siguiente:  
  
```  
int i = 7;  
  
func( i, ++i );  
```  
  
 El lenguaje C++ no garantiza el orden en el que se evalúan los argumentos para una llamada de función. Por consiguiente, en el ejemplo anterior, `func` podría recibir los valores 7 y 8 u 8 y 8 para sus parámetros, dependiendo de si los parámetros se evaluaran de izquierda a derecha o de derecha a izquierda.  
  
## <a name="c-sequence-points-microsoft-specific"></a>Puntos de secuencia de C++ (específicos de Microsoft)  
 Una expresión puede modificar el valor de un objeto solo una vez entre "puntos de secuencia" consecutivos.  
  
 La definición del lenguaje C++ no especifica actualmente puntos de secuencia. Microsoft C++ utiliza los mismos puntos de secuencia que ANSI C para cualquier expresión que contenga operadores de C y que no use operadores sobrecargados. Cuando los operadores están sobrecargados, la semántica cambia de la secuencia de operadores a la secuencia de llamadas de función. Microsoft C++ utiliza los puntos de secuencia siguientes:  
  
-   Operando izquierdo del operador AND lógico (&&). El operando izquierdo del operador AND lógico se evalúa totalmente y se aplican todos los efectos secundarios antes de continuar. No hay ninguna garantía de que se evalúe el operando derecho del operador AND lógico.  
  
-   Operando izquierdo del operador OR lógico (&#124; &#124;). El operando izquierdo del operador OR lógico se evalúa totalmente y se aplican todos los efectos secundarios antes de continuar. No hay ninguna garantía de que se evalúe el operando derecho del operador OR lógico.  
  
-   Operando izquierdo del operador de coma. El operando izquierdo del operador de coma se evalúa totalmente y se aplican todos los efectos secundarios antes de continuar. Los dos operandos del operador de coma se evalúan siempre.  
  
-   Operador de llamada de función. La expresión de llamada de función y todos los argumentos de una función, incluidos los argumentos predeterminados, se evalúan y se aplican todos los efectos secundarios antes de que empiece la función. No hay ningún orden de evaluación específico entre los argumentos o la expresión de llamada de función.  
  
-   Primer operando del operador condicional. El primer operando del operador condicional se evalúa totalmente y se aplican todos los efectos secundarios antes de continuar.  
  
-   El final de una expresión de inicialización completa, como el final de una inicialización en una instrucción de declaración.  
  
-   La expresión de una instrucción de expresión. Las instrucciones de expresión constan de una expresión opcional seguida de un punto y coma (;). La expresión se evalúa completamente para aplicar sus efectos secundarios.  
  
-   La expresión de control en una instrucción de selección (if o switch). La expresión se evalúa completamente y se aplican todos los efectos secundarios antes de que se ejecute el código dependiente de la selección.  
  
-   La expresión de control de una instrucción while o do. La expresión se evalúa completamente y se aplican todos los efectos secundarios antes de que se ejecute alguna instrucción de la siguiente iteración del bucle while o do.  
  
-   Cada una de las tres expresiones de una instrucción for. Cada expresión se evalúa completamente y se aplican todos los efectos secundarios antes de pasar a la siguiente expresión.  
  
-   La expresión de una instrucción return. La expresión se evalúa completamente y se aplican todos los efectos secundarios antes de devolver el control a la función de llamada.  
  
## <a name="see-also"></a>Vea también  
 [Expresiones](../cpp/expressions-cpp.md)
