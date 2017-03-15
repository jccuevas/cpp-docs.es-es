---
title: "Advertencia del compilador (nivel 2) C4146 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4146"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4146"
ms.assetid: d6c31ab1-3120-40d5-8d80-32b5f7046e32
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Advertencia del compilador (nivel 2) C4146
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

operador unario menos aplicado a un tipo unsigned; el resultado aún no tiene signo  
  
 Los tipos unsigned pueden contener sólo valores no negativos, por lo que el operador unario menos \(negación\) no suele tener sentido al aplicarse a un tipo unsigned.  Tanto el operando como el resultado son no negativos.  
  
 En la práctica, esto se produce cuando el programador intenta expresar el valor mínimo de un entero, que es \-2147483648.  Este valor no puede escribirse como \-2147483648 debido a que la expresión se procesa en dos fases:  
  
1.  Se evalúa el número 2147483648.  Debido a que es mayor que el valor de entero máximo de 2147483647, el tipo de 2147483648 no es [int](../../c-language/integer-types.md), sino `unsigned int`.  
  
2.  El operador unario menos se aplica al valor, con un resultado unsigned, el cual también resulta ser 2147483648.  
  
 El tipo unsigned del resultado puede causar un comportamiento inesperado.  Si se utiliza el resultado en una comparación, se puede utilizar una comparación unsigned, por ejemplo, cuando el otro operando es un tipo `int`.  Esto explica por qué el programa de ejemplo siguiente imprime sólo una línea.  
  
 La segunda línea esperada, `1 is greater than the most negative int`, no se imprime porque `((unsigned int)1) > 2147483648`  es false.  
  
 Se puede evitar la advertencia C4146 usando INT\_MIN de limits.h, que tiene el tipo **signed int**.  
  
## Ejemplo  
 El código siguiente genera el error C4146:  
  
```  
// C4146.cpp  
// compile with: /W2  
#include <stdio.h>  
  
void check(int i)   
{  
    if (i > -2147483648)   // C4146  
        printf_s("%d is greater than the most negative int\n", i);  
}  
  
int main()   
{  
    check(-100);  
    check(1);  
}  
```