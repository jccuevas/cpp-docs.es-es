---
title: "_swab | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_swab"
  - "stdlib/_swab"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_swab"
  - "stdlib/_swab"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_swab (función)"
  - "bytes, intercambio"
  - "swab (función)"
  - "intercambio de bytes"
ms.assetid: 017142f2-050c-4f6a-8b49-6b094f58ec94
caps.latest.revision: 18
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _swab
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Intercambia bytes.  
  
## Sintaxis  
  
```  
void _swab(  
   char *src,  
   char *dest,  
   int n   
);  
```  
  
#### Parámetros  
 `src`  
 Datos que se van a copiar o intercambiados.  
  
 `dest`  
 Ubicación de almacenamiento para los datos intercambiados.  
  
 `n`  
 Número de bytes que se van a copiar o intercambiados.  
  
## Comentarios  
 Si `n` es par, la función de `_swab` copia los bytes de `n` de `src`, intercambia cada par de bytes adyacentes, y almacena el resultado en `dest`.  Si `n` es impar, `_swab` copia y cambie los primeros bytes de `n-1` de `src`.  `_swab` se utiliza normalmente para preparar los datos binarios para su transferencia a un equipo que utilice otro orden de bytes.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_swab`|\<stdlib.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_swab.c  
  
#include <stdlib.h>  
#include <stdio.h>  
  
char from[] = "BADCFEHGJILKNMPORQTSVUXWZY";  
char to[] =   "..........................";  
  
int main()  
{  
    printf( "Before: %s\n        %s\n\n", from, to );  
    _swab( from, to, sizeof( from ) );  
    printf( "After:  %s\n        %s\n\n", from, to );  
}  
```  
  
  **Antes: BADCFEHGJILKNMPORQTSVUXWZY**  
 **..........................**  
**A continuación:  BADCFEHGJILKNMPORQTSVUXWZY**  
 **ABCDEFGHIJKLMNOPQRSTUVWXYZ**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)