---
title: "memset, wmemset | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wmemset"
  - "memset"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "memset"
  - "wmemset"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memset (función)"
  - "wmemset (función)"
ms.assetid: e7ceb01b-df69-49c2-b294-a39358ad4699
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# memset, wmemset
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Búferes de conjuntos a un carácter especificado.  
  
## Sintaxis  
  
```  
  
      void *memset(  
   void *dest,  
   int c,  
   size_t count   
);  
wchar_t *wmemset(  
   wchar_t *dest,  
   wchar_t c,  
   size_t count  
);  
```  
  
#### Parámetros  
 *dest*  
 Puntero al destino.  
  
 `c`  
 Carácter el conjunto.  
  
 *count*  
 Número de caracteres.  
  
## Valor devuelto  
 Valor de `dest`.  
  
## Comentarios  
 Establece los primeros caracteres de `count` de `dest` al carácter `c`.  
  
 **Security Note** Asegúrese De que el búfer de destino tiene suficientes caracteres de `count` de sitio por lo menos.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`memset`|\<memory.h\> o \<string.h\>|  
|`wmemset`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_memset.c  
/* This program uses memset to  
 * set the first four chars of buffer to "*".  
 */  
  
#include <memory.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char buffer[] = "This is a test of the memset function";  
  
   printf( "Before: %s\n", buffer );  
   memset( buffer, '*', 4 );  
   printf( "After:  %s\n", buffer );  
}  
```  
  
## Resultados  
  
```  
Before: This is a test of the memset function  
After:  **** is a test of the memset function  
```  
  
 A continuación se muestra un ejemplo de uso de wmemset:  
  
```  
// crt_wmemset.c  
/* This program uses memset to  
 * set the first four chars of buffer to "*".  
 */  
  
#include <wchar.h>  
#include <stdio.h>  
  
int main( void )  
{  
   wchar_t buffer[] = L"This is a test of the wmemset function";  
  
   wprintf( L"Before: %s\n", buffer );  
   wmemset( buffer, '*', 4 );  
   wprintf( L"After:  %s\n", buffer );  
}  
```  
  
## Resultados  
  
```  
Before: This is a test of the wmemset function  
After:  **** is a test of the wmemset function  
```  
  
## Equivalente en .NET Framework  
 [System::Buffer::SetByte](https://msdn.microsoft.com/en-us/library/system.buffer.setbyte.aspx)  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [\_strnset, \_strnset\_l, \_wcsnset, \_wcsnset\_l, \_mbsnset, \_mbsnset\_l](../../c-runtime-library/reference/strnset-strnset-l-wcsnset-wcsnset-l-mbsnset-mbsnset-l.md)