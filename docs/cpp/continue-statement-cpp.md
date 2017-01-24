---
title: "continue (Instrucci&#243;n) (C++) | Microsoft Docs"
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
  - "continue"
  - "continue_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "continue (palabra clave) [C++]"
ms.assetid: 3c94ee57-f732-4c1d-8537-d0ce5382bfd4
caps.latest.revision: 12
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# continue (Instrucci&#243;n) (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Fuerza la transferencia del control a la expresión de control del bucle contenedor [do](../cpp/do-while-statement-cpp.md), [for](../cpp/for-statement-cpp.md) o [while](../cpp/while-statement-cpp.md) más pequeño.  
  
## Sintaxis  
  
```  
continue;  
```  
  
## Comentarios  
 No se ejecuta ninguna de las instrucciones restantes de la iteración actual.  La siguiente iteración del bucle se determina del modo siguiente:  
  
-   En un bucle `do` o `while`, la siguiente iteración se inicia reevaluando la expresión de control de la instrucción `do` o `while`.  
  
-   En un bucle `for` \(que use la sintaxis `for`\(`init-expr`; `cond-expr`; `loop-expr`\)\), se ejecuta la cláusula `loop-expr`.  A continuación, se evalúa de nuevo la cláusula `cond-expr` y, en función del resultado, el bucle finaliza o se produce otra iteración.  
  
 En el ejemplo siguiente se muestra cómo se puede usar la instrucción `continue` para omitir secciones de código e iniciar la siguiente iteración de un bucle.  
  
## Ejemplo  
  
```  
// continue_statement.cpp  
#include <stdio.h>  
int main()  
{  
    int i = 0;  
    do  
    {  
        i++;  
        printf_s("before the continue\n");  
        continue;  
        printf("after the continue, should never print\n");  
     } while (i < 3);  
  
     printf_s("after the do loop\n");  
}  
```  
  
  **antes de continue**  
**antes de continue**  
**antes de continue**  
**después del bucle do**   
## Vea también  
 [Instrucciones de salto](../cpp/jump-statements-cpp.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)