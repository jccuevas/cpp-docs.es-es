---
title: "operador new(CRT) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr110_clr0400.dll"
  - "msvcr100.dll"
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "new[]"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "operator new[]"
  - "vector new"
ms.assetid: 79682f85-6889-40f6-b8f7-9eed5176ea35
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# operador new(CRT)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Asigne el bloque de memoria de montón  
  
## Sintaxis  
  
```  
  
      void *__cdecl operator new[](size_t count);  
void *__cdecl operator new[] (  
   size_t count,   
   void * object  
) throw();  
void *__cdecl operator new[] (  
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
 Este formulario de `operator new` se conoce como vector nuevo, en contraposición al nuevo formulario escalar \([operador nuevo](../c-runtime-library/operator-new-crt.md)\).  
  
 El primer formulario de este operador se conoce como el formulario de nonplacement.  El segundo formato de este operador se conoce como el formato de la posición y el tercer formulario de este operador es el formulario nonthrowing de posición.  
  
 El primer formulario de operador está definido por el compilador y no requiere new.h estar incluido en el programa.  
  
 [operador delete &#91;&#93;](../Topic/operator%20delete\(%3Cnew%3E\).md) libera memoria asignada con el operador new.  
  
 Puede configurar si `operator new[]` devuelve null o produce una excepción en el error.  Vea [Los operadores new y delete](../cpp/new-and-delete-operators.md) para obtener más información.  
  
 A excepción de comportamiento que produce o ninguno\- que produce, CRT `operator new` se comporta como [operador new &#91;&#93;](../Topic/operator%20new\(%3Cnew%3E\).md) en la biblioteca estándar de C\+\+.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`new[]`|\<new.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
 A continuación se muestra cómo utilizar el vector, formulario de nonplacement de `operator new`.  
  
```  
// crt_new4.cpp  
#include <stdio.h>  
int main() {  
   int * k = new int[10];  
   k[0] = 21;  
   printf("%d\n", k[0]);  
   delete [] k;  
}  
```  
  
 A continuación se muestra cómo utilizar el vector, forma de ubicación de `operator new`.  
  
```  
// crt_new5.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * i = new int[10];  
   i[0] = 21;  
   printf("%d\n", i[0]);  
   // initialize existing memory (i) with, in this case, int[[10]  
   int * j = new(i) int[10];   // placement vector new  
   printf("%d\n", j[0]);  
   j[0] = 22;  
   printf("%d\n", i[0]);  
   delete [] i;   // or, could have deleted [] j   
}  
```  
  
 A continuación se muestra cómo utilizar el vector, posición, formulario de ninguno\- captura de `operator new`.  
  
```  
// crt_new6.cpp  
#include <stdio.h>  
#include <new.h>  
int main() {  
   int * k = new(std::nothrow) int[10];  
   k[0] = 21;  
   printf("%d\n", k[0]);  
   delete [] k;  
}  
```  
  
## Vea también  
 [Asignación de memoria](../c-runtime-library/memory-allocation.md)