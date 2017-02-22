---
title: "Advertencia del compilador (nivel 3) C4287 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4287"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4287"
ms.assetid: 1bf3bff8-6402-4d06-95ba-431678a790a7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia del compilador (nivel 3) C4287
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : no coinciden las constantes sin signo o negativas  
  
 Se utilizó una variable sin signo en una operación con un número negativo.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El código siguiente genera el error C4287:  
  
```  
// C4287.cpp  
// compile with: /W3  
#pragma warning(default : 4287)  
#include <stdio.h>  
  
int main()  
{  
    unsigned int u = 1;  
    if (u < -1)   // C4287  
        printf_s("u LT -1");  
    else  
        printf_s("u !LT -1");  
    return 0;  
}  
```