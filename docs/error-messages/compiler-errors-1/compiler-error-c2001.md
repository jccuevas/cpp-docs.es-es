---
title: Compilador Error C2001 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2001
dev_langs:
- C++
helpviewer_keywords:
- C2001
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: aedba438451089aa2d71e06da7ce189ab97d4190
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2001"></a>C2001 de Error del compilador
nueva línea en constante  
  
 Una constante de cadena no se puede continuar en una segunda línea a menos que haga lo siguiente:  
  
-   Finalizar la primera línea con una barra diagonal inversa.  
  
-   La cadena en la primera línea con un signo de comillas dobles de cierre y abra la cadena en la línea siguiente con otro signo de comillas dobles.  
  
 Final de la primera línea con \n no es suficiente.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C2001:  
  
```  
// C2001.cpp  
// C2001 expected  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,  
             world");  
    printf_s("Hello,\n  
             world");  
}  
```  
  
## <a name="example"></a>Ejemplo  
 Se incluyen espacios al principio de la línea siguiente después de un carácter de continuación de línea en la constante de cadena. Ninguno de los ejemplos mostrados anteriormente incrustar un carácter de nueva línea en la constante de cadena. Puede incrustar un carácter de nueva línea como se muestra aquí:  
  
```  
// C2001b.cpp  
#include <stdio.h>  
  
int main()  
{  
    printf_s("Hello,\n\  
             world");  
  
    printf_s("Hello,\  
             \nworld");  
  
    printf_s("Hello,\n"  
             "world");  
  
    printf_s("Hello,"  
             "\nworld");  
  
    printf_s("Hello,"  
             " world");  
  
    printf_s("Hello,\  
             world");  
}  
```
