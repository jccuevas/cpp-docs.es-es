---
title: "Error del compilador C2015 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2015"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2015"
ms.assetid: 8f40af0a-3a5a-4d6a-8ed7-125966e6bfed
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C2015
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

hay demasiados caracteres en la constante  
  
 Hay más de dos caracteres en una constante de carácter.  El límite se establece en un carácter para las constantes de caracteres estándar y en dos para las constantes de caracteres largas.  
  
 Las secuencias de escape como \\t se convierten en un único carácter.  
  
## Ejemplo  
 El código siguiente genera el error C2015:  
  
```  
// C2015.cpp  
// compile with: /c  
  
char test1 = 'error';   // C2015  
char test2 = 'e';   // OK  
```  
  
## Ejemplo  
 C2015 también se puede producir al utilizar una extensión de Microsoft, con constantes de caracteres convertidas a números enteros.  El código siguiente genera el error C2015:  
  
```  
// C2015b.cpp  
#include <stdio.h>  
  
int main()   
{  
    int a = 'abcde';   // C2015  
  
    int b = 'a';   // 'a' = ascii 0x61  
    printf_s("%x\n", b);  
}  
```