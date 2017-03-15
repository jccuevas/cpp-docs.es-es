---
title: "__min | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__min"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__min"
  - "min"
  - "_min"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__min (macro)"
  - "_min (macro)"
  - "min (macro)"
  - "minimum (macro)"
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# __min
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Devuelve el menor de dos valores.  
  
## Sintaxis  
  
```  
type __min(  
   type a,  
   type b   
);  
```  
  
#### Parámetros  
 `type`  
 Cualquier tipo de datos numérico.  
  
 `a, b`  
 Valores de tipo numérico que se va a comparar.  
  
## Valor devuelto  
 El menor de los dos argumentos.  
  
## Comentarios  
 La macro de `__min` compara dos valores y devuelve el valor de menor.  Los argumentos pueden ser de cualquier tipo de datos numérico, con signo o sin signo.  Los argumentos y el valor devuelto deben ser del mismo tipo de datos.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`__min`|\<stdlib.h\>|  
  
## Ejemplo  
  
```  
// crt_minmax.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int a = 10;  
   int b = 21;  
  
   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );  
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );  
}  
```  
  
  **El mayor de 10 y 21 es 21**  
**El menor de 10 y 21 es 10**   
## Equivalente en .NET Framework  
 [System::Math::Min](https://msdn.microsoft.com/en-us/library/system.math.min.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_\_max](../../c-runtime-library/reference/max.md)