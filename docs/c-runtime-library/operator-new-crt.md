---
title: "operator new (CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr90.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator new"
  - "escalar new"
ms.assetid: 4ae51618-a4e6-4172-b324-b99d86d1bdca
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operator new (CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigna el bloque de memoria de montón  
  
## Sintaxis  
  
```  
  
      void *__cdecl operator new(  
   size_t count  
);  
void *__cdecl operator new(  
   size_t count,   
   void * object  
) throw();  
void *__cdecl operator new(  
   size_t count,   
   const std::nothrow_t&  
) throw();  
```  
  
#### Parámetros  
 *count*  
 El tamaño de la asignación.  
  
 *objeto*  
 Un puntero a un bloque de memoria en el que el objeto se creará.  
  
## Valor devuelto  
 Un puntero a la dirección de byte inferior de almacenamiento recién asignado.  
  
## Comentarios  
 Este formulario de `operator new` se conoce como nuevo escalar, en contraposición al nuevo formulario de vector \([operador new &#91;&#93;](../c-runtime-library/new-operator-crt.md)\).  
  
 El primer formulario de este operador se conoce como el formulario de nonplacement.  El segundo formato de este operador se conoce como el formato de la posición y el tercer formulario de este operador es el nonthrowing, forma de ubicación.  
  
 El primer formulario de operador está definido por el compilador y no requiere new.h estar incluido en el programa.  
  
 [operador delete](../c-runtime-library/operator-delete-crt.md) libera memoria asignada con `operator new`.  
  
 Puede configurar si el operador new devuelve null o produce una excepción en el error.  Vea [Los operadores new y delete](../cpp/new-and-delete-operators.md) para obtener más información.  
  
 A excepción de comportamiento que produce o ninguno\- que produce, CRT `operator new` se comporta como [operador nuevo](../Topic/operator%20new%20\(%3Cnew%3E\).md) en la biblioteca estándar de C\+\+.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|**new**|\<new.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 A continuación se muestra cómo utilizar el escalar, formulario de nonplacement de `operator new`.  
  
```  
// crt_new1.cpp  
#include <stdio.h>  
int main() {  
   int * i = new int(6);  
   printf("%d\n", *i);  
   delete i;  
}  
```  
  
 A continuación se muestra cómo utilizar el escalar, forma de ubicación de `operator new`.  
  
```  
// crt_new2.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * i = new int(12);  
   printf("*i = %d\n", *i);  
   // initialize existing memory (i) with, in this case, int(7)  
   int * j = new(i) int(7);   // placement new  
   printf("*j = %d\n", *j);  
   printf("*i = %d\n", *i);  
   delete i;   // or, could have deleted j  
}  
```  
  
 A continuación se muestra cómo utilizar el escalar, posición, formulario de ninguno\- captura de `operator new`.  
  
```  
// crt_new3.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   // allocates memory, initialize (8) and if call fails, new returns null  
   int * k = new(std::nothrow) int(8);   // placement new  
   printf("%d\n", *k);  
   delete k;  
}  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Asignación de memoria](../c-runtime-library/memory-allocation.md)