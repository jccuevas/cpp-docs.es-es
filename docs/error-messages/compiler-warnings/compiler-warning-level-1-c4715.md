---
title: "Advertencia del compilador (nivel 1) C4715 | Microsoft Docs"
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
  - "C4715"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4715"
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4715
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : no todas las rutas de acceso de control devuelven un valor  
  
 La función especificada podría no devolver un valor.  
  
## Ejemplo  
  
```  
// C4715a.cpp  
// compile with: /W1 /LD  
int func1( int i )  
{  
   if( i )  
   return 3;  // C4715 warning, nothing returned if i == 0  
}  
```  
  
 Para evitar esta advertencia, modifique el código de forma que todas las rutas de acceso asignen un valor devuelto a la función:  
  
```  
// C4715b.cpp  
// compile with: /LD  
int func1( int i )  
{  
   if( i ) return 3;  
   else return 0;     // OK, always returns a value  
}  
```  
  
 Es posible que el código contenga una llamada a una función que nunca devuelva ningún valor, como en el siguiente ejemplo:  
  
```  
// C4715c.cpp  
// compile with: /W1 /LD  
void fatal()  
{  
}  
int glue()  
{  
   if(0)  
      return 1;  
   else if(0)  
      return 0;  
   else  
      fatal();   // C4715  
}  
```  
  
 Este código también genera una advertencia, ya que el compilador no sabe que `fatal` no devuelve ningún valor.  Para evitar que este tipo de código genere un mensaje de error, declare `fatal` usando [\_\_declspec\(noreturn\)](../../cpp/noreturn.md).