---
title: "memcpy, wmemcpy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "memcpy"
  - "wmemcpy"
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
  - "wmemcpy"
  - "memcpy"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "memcpy (función)"
  - "wmemcpy (función)"
ms.assetid: 34abb90b-bffb-46dc-a2f3-a5e9940839d6
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# memcpy, wmemcpy
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Copia bytes entre búferes.  Hay disponibles versiones más seguras de estas funciones; vea [memcpy\_s, wmemcpy\_s](../../c-runtime-library/reference/memcpy-s-wmemcpy-s.md).  
  
## Sintaxis  
  
```  
void *memcpy(  
   void *dest,  
   const void *src,  
   size_t count   
);  
wchar_t *wmemcpy(  
   wchar_t *dest,  
   const wchar_t *src,  
   size_t count  
);  
```  
  
#### Parámetros  
 `dest`  
 Nuevo búfer.  
  
 `src`  
 Búfer del que copiar.  
  
 `count`  
 Número de caracteres que se copiará.  
  
## Valor devuelto  
 El valor de `dest`.  
  
## Comentarios  
 `memcpy` copia `count` bytes de `src` a `dest`; `wmemcpy` copia `count` caracteres anchos \(dos bytes\).  Si el origen y el destino se superponen, el comportamiento de `memcpy` no está definido.  Use `memmove` para controlar las áreas superpuestas.  
  
> [!IMPORTANT]
>  Asegúrese de que el búfer de destino sea del mismo tamaño o mayor que el búfer de origen.  Para obtener más información, vea [Evitar saturaciones del búfer](http://msdn.microsoft.com/library/windows/desktop/ms717795).  
  
> [!IMPORTANT]
>  Dado que se ha determinado que muchas saturaciones de búferes \(posibles vulnerabilidades de seguridad\) se deben a un uso inapropiado de `memcpy`, esta función se cuenta entre las "prohibidas" por el ciclo de vida de desarrollo de seguridad \(SDL\).  Observará que algunas clases de biblioteca de VC \+\+ siguen utilizando `memcpy`.  Además, verá que el optimizador del compilador de VC \+\+ emite en ocasiones llamadas a `memcpy`.  El producto Visual C\+\+ se desarrolla de acuerdo con el proceso SDL, por lo que se ha evaluado con cuidado el uso de esta función prohibida.  En el caso de su uso por parte de bibliotecas, se han examinado meticulosamente las llamadas para garantizar que no provoquen saturaciones de búferes.  En el caso del compilador, determinados patrones de código se reconocen en ocasiones como idénticos al patrón de `memcpy`, y por tanto se reemplazan con una llamada a la función.  En tales casos, el uso de `memcpy` no es menos seguro de lo que hubieran sido las instrucciones originales; estas simplemente se han optimizado como una llamada a la función `memcpy` para mejorar el rendimiento.  Al igual que el uso de funciones de CRT "seguras" no garantiza la seguridad \(solo dificulta la falta de seguridad\), el uso de funciones "prohibidas" no garantiza el peligro \(solo se requiere un mayor escrutinio para garantizar la seguridad\).  
>   
>  Dado que el uso de `memcpy` por parte del compilador y las bibliotecas de VC \+\+ está tan estudiado, se permiten estas llamadas dentro del código sin perder la conformidad con SDL.  Las llamadas a `memcpy` en el código fuente de la aplicación solo son conformes a SDL si las han revisado expertos en seguridad.  
  
 Las funciones `memcpy` y `wmemcpy` solo quedarán desusadas si la constante `_CRT_SECURE_DEPRECATE_MEMORY` se define antes de la declaración de inclusión, como en el ejemplo siguiente:  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <memory.h>  
```  
  
 o  
  
```  
#define _CRT_SECURE_DEPRECATE_MEMORY  
#include <wchar.h>  
```  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`memcpy`|\<memory.h\> o \<string.h\>|  
|`wmemcpy`|\<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
 Vea en [memmove](../../c-runtime-library/reference/memmove-wmemmove.md) un ejemplo de cómo usar `memcpy`.  
  
## Vea también  
 [Manipulación del búfer](../../c-runtime-library/buffer-manipulation.md)   
 [\_memccpy](../../c-runtime-library/reference/memccpy.md)   
 [memchr, wmemchr](../../c-runtime-library/reference/memchr-wmemchr.md)   
 [memcmp, wmemcmp](../../c-runtime-library/reference/memcmp-wmemcmp.md)   
 [memmove, wmemmove](../../c-runtime-library/reference/memmove-wmemmove.md)   
 [memset, wmemset](../../c-runtime-library/reference/memset-wmemset.md)   
 [strcpy\_s, wcscpy\_s, \_mbscpy\_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)   
 [strncpy\_s, \_strncpy\_s\_l, wcsncpy\_s, \_wcsncpy\_s\_l, \_mbsncpy\_s, \_mbsncpy\_s\_l](../../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)