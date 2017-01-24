---
title: "__restrict | Microsoft Docs"
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
  - "__restrict"
  - "__restrict_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__restrict (palabra clave) [C++]"
ms.assetid: 2d151b4d-f930-49df-bd16-d8757ec7fa83
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# __restrict
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como el modificador **\_\_declspec \([restrict](../cpp/restrict.md)\)**, la palabra clave `__restrict` indica que un símbolo no tiene un alias en el ámbito actual.  La palabra clave `__restrict` difiere del modificador `__declspec ( restrict )` en lo siguiente:  
  
-   La palabra clave `__restrict` solo es válida en variables y `__declspec ( restrict )` solo es válido en declaraciones de función y definiciones.  
  
-   `__restrict` es similar a `restrict` de la especificación C99, pero `__restrict` se puede utilizar en programas de C\+\+ o C.  
  
-   Cuando se utiliza `__restrict`, el compilador no propagará la propiedad sin alias de una variable.  Es decir, si se asigna una variable `__restrict` a una variable que no es `__restrict`, el compilador seguirá permitiendo que la variable que no es \_\_restrict tenga un alias.  Este comportamiento es diferente del de la palabra clave `restrict` de la especificación C99.  
  
 Normalmente, si se modifica el comportamiento de una función completa, es mejor usar `__declspec ( restrict )` que la palabra clave.  
  
 En Visual Studio de 2015 y versiones posteriores, se puede usar `__restrict` en las referencias de C\+\+.  
  
> [!NOTE]
>  Cuando se usa en una variable que tiene también la palabra clave [volatile](../cpp/volatile-cpp.md), `volatile` tendrá prioridad.  
  
## Ejemplo  
  
```  
// __restrict_keyword.c  
// compile with: /LD  
// In the following function, declare a and b as disjoint arrays  
// but do not have same assurance for c and d.  
void sum2(int n, int * __restrict a, int * __restrict b,   
          int * c, int * d) {  
   int i;  
   for (i = 0; i < n; i++) {  
      a[i] = b[i] + c[i];  
      c[i] = b[i] + d[i];  
    }  
}  
  
// By marking union members as __restrict, tell compiler that  
// only z.x or z.y will be accessed in any given scope.  
union z {  
   int * __restrict x;  
   double * __restrict y;  
};  
```  
  
## Vea también  
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)