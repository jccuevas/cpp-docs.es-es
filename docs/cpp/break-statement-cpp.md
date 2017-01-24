---
title: "break (Instrucci&#243;n) (C++) | Microsoft Docs"
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
  - "break_cpp"
  - "break"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "break (palabra clave) [C++]"
ms.assetid: 63739928-8985-4b05-93ce-016322e6da3d
caps.latest.revision: 13
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# break (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La instrucción `break` finaliza la ejecución del bucle o la instrucción condicional envolvente más próximo en el que aparece.  El control pasa a la instrucción que hay a continuación del final de la instrucción, si hay alguna.  
  
## Sintaxis  
  
```  
break;  
```  
  
## Comentarios  
 La instrucción `break` se utiliza con la instrucción condicional [switch](../cpp/switch-statement-cpp.md) y con las instrucciones de bucle [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md) y [while](../cpp/while-statement-cpp.md).  
  
 En una instrucción `switch`, la instrucción `break` hace que el programa ejecute la siguiente instrucción que hay fuera de la instrucción `switch`.  Sin una instrucción `break`, se ejecutan todas las instrucciones que hay desde la etiqueta `case` coincidente hasta el final de la instrucción `switch`, incluida la cláusula `default`.  
  
 En los bucles, la instrucción `break` finaliza la ejecución de la instrucción envolvente `do`, `for` o `while` más próxima.  El control pasa a la instrucción que hay a continuación de la instrucción finalizada, si hay alguna.  
  
 Dentro de instrucciones anidadas, la instrucción `break` finaliza solo la instrucción `do`, `for`, `switch` o `while` que la envuelve inmediatamente.  Puede utilizar una instrucción `return` o `goto` para transferir el control desde estructuras más anidadas.  
  
## Ejemplo  
 En el código siguiente se muestra cómo usar la instrucción `break` en un bucle `for`.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
int main()  
{  
    // An example of a standard for loop  
    for (int i = 1; i < 10; i++)  
    {  
        cout << i << '\n';  
        if (i == 4)  
            break;  
    }  
  
    // An example of a range-based for loop  
int nums []{1, 2, 3, 4, 5, 6, 7, 8, 9, 10};  
  
    for (int i : nums) {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
    }  
}  
```  
  
  **En cada caso:**   
**1**  
**2**  
**3** En el código siguiente se muestra cómo usar `break` en un bucle `while` y un bucle `do`.  
  
```cpp  
  
#include <iostream>  
using namespace std;  
  
int main() {  
    int i = 0;  
  
    while (i < 10) {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
        i++;  
    }  
  
    i = 0;  
    do {  
        if (i == 4) {  
            break;  
        }  
        cout << i << '\n';  
        i++;  
    } while (i < 10);  
}  
```  
  
  **En cada caso:**  
**0**  
**1**  
**2**  
**3** En el código siguiente se muestra cómo usar `break` en una instrucción switch.  Debe usar `break` en todos los casos si desea tratar cada caso por separado; si no emplea `break`, la ejecución de código pasa al caso siguiente.  
  
```cpp  
#include <iostream>  
using namespace std;  
  
enum Suit{ Diamonds, Hearts, Clubs, Spades };  
  
int main() {  
  
    Suit hand;  
    . . .  
    // Assume that some enum value is set for hand  
    // In this example, each case is handled separately  
    switch (hand)  
    {  
    case Diamonds:  
        cout << "got Diamonds \n";  
        break;  
    case Hearts:  
        cout << "got Hearts \n";  
        break;  
    case Clubs:  
        cout << "got Clubs \n";  
        break;  
    case Spades:  
        cout << "got Spades \n";  
        break;  
    default:   
          cout << "didn't get card \n";  
    }  
    // In this example, Diamonds and Hearts are handled one way, and  
    // Clubs, Spades, and the default value are handled another way  
    switch (hand)  
    {  
    case Diamonds:  
    case Hearts:  
        cout << "got a red card \n";  
        break;  
    case Clubs:  
    case Spades:   
    default:  
        cout << "didn't get a red card \n";  
    }  
}  
```  
  
## Vea también  
 [Instrucciones de salto](../cpp/jump-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)   
 [continue \(Instrucción\)](../cpp/continue-statement-cpp.md)