---
title: "La utilizaci&#243;n de un nombre de funci&#243;n sin () no genera c&#243;digo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones [C++], sin paréntesis"
ms.assetid: edf4a177-a160-44aa-8436-e077b5b27809
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# La utilizaci&#243;n de un nombre de funci&#243;n sin () no genera c&#243;digo
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Cuando se utiliza sin paréntesis un nombre de función declarado en el programa, el compilador no produce código.  Esto ocurrirá independientemente de si la función utiliza o no parámetros, ya que el compilador calcula la dirección de la función; sin embargo, como el operador de llamada a la función "\(\)" no está presente, no se realiza ninguna llamada.  El resultado es similar al siguiente:  
  
```  
// compile with /Wall to generate a warning  
int a;  
a;      // no code generated here either  
```  
  
 En Visual C\+\+, no se generan resultados de diagnóstico ni al utilizar el nivel 4 de advertencia.  No se emite ninguna advertencia y no se produce código.  
  
 El código de ejemplo siguiente se compila \(con una advertencia\) y vincula correctamente sin error, pero no produce código relacionado con `funcn( )`.  Para que esto funcione correctamente, debe agregar el operador de llamada a función "\(\)".  
  
```  
#include <stdio.h>  
void funcn();  
  
int main() {  
   funcn;      /* missing function call operator;   
                  call will fail.  Use funcn() */  
   }  
  
void funcn() {  
   printf("\nHello World\n");  
}  
```  
  
## Vea también  
 [Optimizar el código](../../build/reference/optimizing-your-code.md)