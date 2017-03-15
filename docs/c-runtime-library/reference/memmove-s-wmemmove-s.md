---
title: "memmove_s, wmemmove_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wmemmove_s"
  - "memmove_s"
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
  - "api-ms-win-crt-string-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "wmemmove_s"
  - "memmove_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memmove_s (función)"
  - "wmemmove_s (función)"
ms.assetid: a17619e4-1307-4bb0-98c6-77f8c68dab2d
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# memmove_s, wmemmove_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Mueve un búfer a otro.  Estas versiones de [memmove, wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
  
      errno_t memmove_s(  
   void *dest,  
   size_t numberOfElements,  
   const void *src,  
   size_t count  
);  
errno_t wmemmove_s(  
   wchar_t *dest,  
   size_t numberOfElements,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### Parámetros  
 `dest`  
 Objeto de destino.  
  
 `numberOfElements`  
 Tamaño del búfer de destino.  
  
 `src`  
 Objeto de origen.  
  
 `count`  
 Número de bytes \(`memmove_s`\) o de caracteres \(`wmemmove_s`\) para copiar.  
  
## Valor devuelto  
 Cero si correctamente; un código de error del error  
  
### Condiciones de error  
  
|`dest`|`numberOfElements`|`src`|Valor devuelto|Contenido de `dest`|  
|------------|------------------------|-----------|--------------------|-------------------------|  
|`NULL`|any|any|`EINVAL`|no modificado|  
|any|any|`NULL`|`EINVAL`|no modificado|  
|any|\< `count`|any|`ERANGE`|no modificado|  
  
## Comentarios  
 Copia los bytes de `count` de caracteres de `src` a *`dest`.* Si algunas regiones de origen y de destino se superponen, `memmove_s` garantiza que los bytes de origen originales en la región que se superpone se copiarán antes de ser sobrescrito.  
  
 Si `dest` o si `src` es un puntero null, o si la cadena de destino es demasiado pequeño, estas funciones invoca un controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md) .  Si la ejecución puede continuar, estas funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`memmove_s`|\<string.h\>|  
|`wmemmove_s`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_memmove_s.c  
//  
// The program demonstrates the   
// memmove_s function which works as expected  
// for moving overlapping regions.  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   char str[] = "0123456789";  
  
   printf("Before: %s\n", str);  
  
   // Move six bytes from the start of the string  
   // to a new position shifted by one byte. To protect against  
   // buffer overrun, the secure version of memmove requires the  
   // the length of the destination string to be specified.   
  
   memmove_s((str + 1), strnlen(str + 1, 10), str, 6);   
  
   printf_s(" After: %s\n", str);  
}  
```  
  
## Resultados  
  
```  
Before: 0123456789  
 After: 0012345789  
```  
  
## Equivalente en .NET Framework  
 [System::Buffer::BlockCopy](https://msdn.microsoft.com/en-us/library/system.buffer.blockcopy.aspx)  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)   
 [strcpy\_s, wcscpy\_s, \_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)