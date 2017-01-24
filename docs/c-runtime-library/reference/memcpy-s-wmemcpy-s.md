---
title: "memcpy_s, wmemcpy_s | Microsoft Docs"
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
  - "memcpy_s"
  - "wmemcpy_s"
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
  - "wmemcpy_s"
  - "memcpy_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "memcpy_s (función)"
  - "wmemcpy_s (función)"
ms.assetid: 5504e20a-83d9-4063-91fc-3f55f7dabe99
caps.latest.revision: 27
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# memcpy_s, wmemcpy_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copia bytes entre búferes. Estas son versiones de [memcpy, wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md) con mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t memcpy_s(  
   void *dest,  
   size_t destSize,  
   const void *src,  
   size_t count   
);  
errno_t wmemcpy_s(  
   wchar_t *dest,  
   size_t destSize,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### Parámetros  
 `dest`  
 Nuevo búfer.  
  
 `destSize`  
 Tamaño del búfer de destino, en bytes de los caracteres anchos \(wchar\_t\) para wmemcpy\_s memcpy\_s.  
  
 `src`  
 Búfer del que copiar.  
  
 `count`  
 Número de caracteres que se copiará.  
  
## Valor devuelto  
 Devuelve cero si se ejecuta correctamente; devuelve un código de error si se produce un error.  
  
### Condiciones de error  
  
|`dest`|`destSize`|`src`|Valor devuelto|Contenido de `dest`|  
|------------|----------------|-----------|--------------------|-------------------------|  
|`NULL`|any|any|`EINVAL`|no modificado|  
|any|any|`NULL`|`EINVAL`|`dest` se pone a cero|  
|any|\< `count`|any|`ERANGE`|`dest` se pone a cero|  
  
## Comentarios  
 `memcpy_s` copia `count` bytes de `src` a `dest`; `wmemcpy_s` copia `count` caracteres anchos \(dos bytes\). Si el origen y el destino se superponen, el comportamiento de `memcpy_s` no está definido. Use `memmove_s` para controlar las áreas superpuestas.  
  
 Estas funciones validan sus parámetros. Si `dest` o `src` es un puntero nulo, o `destSize` es menor que `count`, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `EINVAL` y establecen `errno` en `EINVAL`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`memcpy_s`|\<memory.h\> o \<string.h\>|  
|`wmemcpy_s`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_memcpy_s.c  
// Copy memory in a more secure way.  
  
#include <memory.h>  
#include <stdio.h>  
  
int main()  
{  
   int a1[10], a2[100], i;  
   errno_t err;  
  
   // Populate a2 with squares of integers  
   for (i = 0; i < 100; i++)  
   {  
      a2[i] = i*i;  
   }  
  
   // Tell memcpy_s to copy 10 ints (40 bytes), giving  
   // the size of the a1 array (also 40 bytes).  
   err = memcpy_s(a1, sizeof(a1), a2, 10 * sizeof (int) );      
   if (err)  
   {  
      printf("Error executing memcpy_s.\n");  
   }  
   else  
   {  
     for (i = 0; i < 10; i++)  
       printf("%d ", a1[i]);  
   }  
   printf("\n");  
}  
```  
  
```Output  
0 1 4 9 16 25 36 49 64 81   
```  
  
## Equivalente en .NET Framework  
 No disponible. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove, wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy, wcscpy, \_mbscpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)   
 [strncpy, \_strncpy\_l, wcsncpy, \_wcsncpy\_l, \_mbsncpy, \_mbsncpy\_l](../../c-runtime-library/reference/strncpy-strncpy-l-wcsncpy-wcsncpy-l-mbsncpy-mbsncpy-l.md)   
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)