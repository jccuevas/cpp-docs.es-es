---
title: "Error del compilador C2001 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2001"
ms.assetid: 0c3a7821-d8e5-4398-ab5a-4116d46e8dda
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

nueva línea en constante  
  
 Una constante de cadena no puede continuarse en una segunda línea a menos que se haga lo siguiente:  
  
-   Terminar la primera línea con una barra diagonal inversa \(\\\).  
  
-   Cerrar la cadena de la primera línea con un signo de comillas dobles \("\) y abrir la cadena de la línea siguiente con el mismo signo.  
  
 No basta con terminar la primera línea con \\n.  
  
## Ejemplo  
 El código siguiente genera el error C2001:  
  
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
  
## Ejemplo  
 Los espacios al principio de la línea inmediatamente después de un carácter de continuación de línea se incluyen en la constante de cadena.  Ninguno de los ejemplos anteriores inserta un carácter de nueva línea en la constante de cadena.  A continuación se indica la forma de insertar un carácter de nueva línea:  
  
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