---
title: "for (Instrucci&#243;n) (C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "for (palabra clave) [C++]"
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# for (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ejecuta una instrucción repetidamente hasta que la condición es false.  Para obtener información sobre la instrucción for basada en intervalo, vea [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md).  
  
## Sintaxis  
  
```  
for ( init-expression ; cond-expression ; loop-expression )   
    statement;  
```  
  
## Comentarios  
 La instrucción `for` se utiliza para construir bucles que deben ejecutarse un número especificado de veces.  
  
 La instrucción `for` consta de tres partes opcionales, como se muestra en la tabla siguiente.  
  
### para los elementos de bucle  
  
|Nombre de la sintaxis|Cuándo se ejecuta|Descripción|  
|---------------------------|-----------------------|-----------------|  
|`init-expression`|Antes que cualquier otro elemento de la instrucción **for**, `init-expression` solo se ejecuta una vez.  El control pasa entonces a `cond-expression`.|Se suele utilizar para inicializar índices de bucle.  Puede contener expresiones o declaraciones.|  
|`cond-expression`|Antes de la ejecución de cada iteración de `statement`, incluida la primera iteración.  `statement` solo se ejecuta si `cond-expression` se evalúa como true \(distinto de cero\).|Expresión que se evalúa como un tipo entero o un tipo de clase que tiene una conversión no ambigua a un tipo entero.  Se utiliza normalmente para comprobar los criterios de finalización del bucle.|  
|`loop-expression`|Al final de cada iteración de `statement`.  Después de ejecutarse `loop-expression`, se evalúa `cond-expression`.|Se utiliza normalmente para incrementar índices de bucle.|  
  
 En los ejemplos siguientes se muestran distintas formas de usar la instrucción `for`.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main() {  
    // The counter variable can be declared in the init-expression.  
    for (int i = 0; i < 2; i++ ){   
       cout << i;  
    }  
    // Output: 01  
    // The counter variable can be declared outside the for loop.  
    int i;  
    for (i = 0; i < 2; i++){  
        cout << i;  
    }  
    // Output: 01  
    // These for loops are the equivalent of a while loop.  
    i = 0;  
    while (i < 2){  
        cout << i++;  
    }  
}  
    // Output: 012  
```  
  
 `init-expression` y `loop-expression` pueden contener varias instrucciones separadas por comas.  Por ejemplo:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
    int i, j;  
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {  
        cout << "i + j = " << (i + j) << '\n';  
    }  
}  
    // Output:  
    i + j = 15  
    i + j = 17  
    i + j = 19  
```  
  
 `loop-expression` se puede aumentar o reducir, o modificar de otras maneras.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main(){  
for (int i = 10; i > 0; i--) {  
        cout << i << ' ';  
    }  
    // Output: 10 9 8 7 6 5 4 3 2 1  
    for (int i = 10; i < 20; i = i+2) {  
        cout << i << ' ';  
    }  
    // Output: 10 12 14 16 18  
```  
  
 Un bucle `for` finaliza cuando se ejecuta una instrucción [break](../cpp/break-statement-cpp.md), [return](../cpp/return-statement-cpp.md) o [goto](../cpp/goto-statement-cpp.md) \(en una instrucción con etiqueta fuera del bucle **for**\) dentro de `statement`.  Una instrucción [continue](../cpp/continue-statement-cpp.md) en un bucle `for` solo finaliza la iteración actual.  
  
 Si se omite `cond-expression`, se considera true y el bucle **for** no finaliza sin una instrucción `break`, `return` o `goto` dentro de `statement`.  
  
 Aunque los tres campos de la instrucción `for` se suelen utilizar para la inicialización, comprobar la finalización y el incremento, no se limitan a estos usos.  Por ejemplo, el código siguiente imprime los números de 0 a 4.  En este caso, `statement` es la instrucción NULL:  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    int i;  
    for( i = 0; i < 5; cout << i << '\n', i++){  
        ;  
    }  
}  
```  
  
## Bucles for y el estándar de C\+\+  
 El estándar de C\+\+ indica que una variable declarada en un bucle `for` saldrá del ámbito cuando finalice el bucle `for`.  Por ejemplo:  
  
```cpp  
for (int i = 0 ; i < 5 ; i++) {  
   // do something  
}  
// i is now out of scope under /Za or /Zc:forScope  
```  
  
 De forma predeterminada, en [\/Ze](../build/reference/za-ze-disable-language-extensions.md), una variable declarada en un bucle `for` permanece en el ámbito hasta que finaliza el ámbito de inclusión del bucle `for`.  
  
 [\/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) habilita el comportamiento estándar de las variables declaradas en bucles for sin necesidad de especificar \/Za.  
  
 También es posible utilizar las diferencias de ámbito del bucle `for` para volver a declarar variables en \/Ze de la manera siguiente:  
  
```cpp  
// for_statement5.cpp  
int main(){  
   int i = 0;   // hidden by var with same name declared in for loop  
   for ( int i = 0 ; i < 3; i++ ) {}  
  
   for ( int i = 0 ; i < 3; i++ ) {}  
}  
```  
  
 Esto imita mejor el comportamiento estándar de una variable declarada en un bucle `for`, que requiere que las variables declaradas en un bucle `for` salgan del ámbito cuando finalice el bucle.  Cuando una variable se declara en un bucle `for`, el compilador la promueve internamente a una variable local en el ámbito de inclusión del bucle `for` incluso aunque ya exista una variable local con el mismo nombre.  
  
## Vea también  
 [Instrucciones de iteración](../cpp/iteration-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [while \(Instrucción\) \(C\+\+\)](../cpp/while-statement-cpp.md)   
 [do\-while \(instrucción de C\+\+\)](../cpp/do-while-statement-cpp.md)   
 [Instrucción for basada en intervalo \(C\+\+\)](../cpp/range-based-for-statement-cpp.md)