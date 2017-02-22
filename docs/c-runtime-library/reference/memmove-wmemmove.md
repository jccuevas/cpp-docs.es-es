---
title: "memmove, wmemmove | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "memmove"
  - "wmemmove"
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
  - "ntdll.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "memmove"
  - "wmemmove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memmove (función)"
  - "wmemmove (función)"
ms.assetid: 3a906114-9cf3-40d7-bd99-ee452004f218
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# memmove, wmemmove
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Mueve un búfer a otro.  Hay disponibles versiones más seguras de estas funciones; vea [memmove\_s, wmemmove\_s](../../c-runtime-library/reference/memmove-s-wmemmove-s.md).  
  
## Sintaxis  
  
```  
void *memmove(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemmove(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### Parámetros  
 `dest`  
 Objeto de destino.  
  
 `src`  
 Objeto de origen.  
  
 `count`  
 Número de bytes \(`memmove`\) o de caracteres \(`wmemmove`\) para copiar.  
  
## Valor devuelto  
 El valor de *`dest`.*  
  
## Comentarios  
 Bytes de `count` de copias \(`memmove`\) o caracteres \(`wmemmove`\) de `src` a *`dest`.* Si algunas regiones de origen y de destino se superponen, ambas funciones garantizan que los bytes de origen originales en la región que se superpone se copiarán antes de ser sobrescrito.  
  
 **Security Note** Asegúrese De que el búfer de destino es el mismo tamaño o mayor que el búfer de origen.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
 Las funciones de `memmove` y de `wmemmove` se aplazada de desuso sólo si la constante `_CRT_SECURE_DEPRECATE_MEMORY` se define antes de la instrucción include para que las funciones son aplazada de obsoletos, como en el ejemplo siguiente:  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <string.h>  
or  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`memmove`|\<string.h\>|  
|`wmemmove`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_memcpy.c  
// Illustrate overlapping copy: memmove  
// always handles it correctly; memcpy may handle  
// it correctly.  
//  
  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
  
char str1[7] = "aabbcc";  
  
int main( void )  
{  
   printf( "The string: %s\n", str1 );  
   memcpy( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
  
   strcpy_s( str1, sizeof(str1), "aabbcc" );   // reset string  
  
   printf( "The string: %s\n", str1 );  
   memmove( str1 + 2, str1, 4 );  
   printf( "New string: %s\n", str1 );  
}  
```  
  
  **La cadena: aabbcc**  
**Nueva cadena: aaaabb**  
**La cadena: aabbcc**  
**Nueva cadena: aaaabb**   
## Equivalente en .NET Framework  
 [System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)