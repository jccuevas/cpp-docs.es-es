---
title: "tmpnam_s, _wtmpnam_s | Microsoft Docs"
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
  - "tmpnam_s"
  - "_wtmpnam_s"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "tmpnam_s"
  - "_wtmpnam_s"
  - "L_tmpnam_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_wtmpnam_s (función)"
  - "nombres de archivo [C++], crear temporales"
  - "nombres de archivo [C++], temporal"
  - "L_tmpnam_s (constante)"
  - "archivos temporales, crear"
  - "tmpnam_s (función)"
  - "wtmpnam_s (función)"
ms.assetid: e70d76dc-49f5-4aee-bfa2-f1baa2bcd29f
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# tmpnam_s, _wtmpnam_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genere los nombres que puede utilizar para crear los archivos temporales.  Éstas son versiones de [tmpnam y \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t tmpnam_s(  
   char * str,  
   size_t sizeInChars   
);  
errno_t _wtmpnam_s(  
   wchar_t *str,  
   size_t sizeInChars   
);  
template <size_t size>  
errno_t tmpnam_s(  
   char (&str)[size]  
); // C++ only  
template <size_t size>  
errno_t _wtmpnam_s(  
   wchar_t (&str)[size]  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `str`  
 Puntero que contendrá el nombre generado.  
  
 \[in\] `sizeInChars`  
 El tamaño del búfer en caracteres.  
  
## Valor devuelto  
 Ambas funciones devuelven 0 si correctamente o un número de error en el error.  
  
### Condiciones de error  
  
|||||  
|-|-|-|-|  
|`str`|`sizeInChars`|**Valor devuelto**|**Contents of**  `str`|  
|`NULL`|any|`EINVAL`|no modificado|  
|no `NULL` \(señala memoria válido\)|demasiado corto|`ERANGE`|no modificado|  
  
 Si `str` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven `EINVAL`.  
  
## Comentarios  
 Cada una de estas funciones devuelve el nombre de un archivo que no existe actualmente.  `tmpnam_s` devuelve un nombre único en el directorio de trabajo actual.  La nota a un nombre de archivo con por una barra diagonal inversa y ninguna información de la ruta de acceso, como \\fname21, esto indica que el nombre es válido para el directorio de trabajo actual.  
  
 Para `tmpnam_s`, puede almacenar este nombre de archivo generado en `str`.  La longitud máxima de una cadena devuelta por `tmpnam_s` es `L_tmpnam_s`, definido en STDIO.H.  Si `str` es `NULL`, después `tmpnam_s` deja el resultado en un buffer estático interno.  Para cualquier llamada subsiguiente destruye este valor.  El nombre generado por `tmpnam_s` consta de un nombre de archivo programa\- generado y, después de la primera llamada a `tmpnam_s`, una extensión de archivo números secuenciales en base 32 \(.1\-.1vvvvvu, cuando `TMP_MAX_S` en STDIO.H es INT\_MAX\).  
  
 `tmpnam_s` controla automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos OEM obtenida del sistema operativo.  `_wtmpnam_s` es una versión con caracteres anchos de `tmpnam_s`; el argumento y el valor devuelto de `_wtmpnam_s` son cadenas de caracteres anchos.  `_wtmpnam_s` y `tmpnam_s` se comportan exactamente igual excepto que `_wtmpnam_s` no controla las cadenas de multibyte\- carácter.  
  
 En C\+\+, el uso de estas funciones se simplifica mediante sobrecargas de plantilla. Las sobrecargas pueden deducir la longitud del búfer automáticamente, lo que elimina la necesidad de especificar un argumento de tamaño.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ttmpnam_s`|`tmpnam_s`|`tmpnam_s`|`_wtmpnam_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`tmpnam_s`|\<stdio.h\>|  
|`_wtmpnam_s`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_tmpnam_s.c  
// This program uses tmpnam_s to create a unique filename in the  
// current working directory.   
//  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char name1[L_tmpnam_s];  
   errno_t err;  
   int i;  
  
   for (i = 0; i < 15; i++)  
   {  
      err = tmpnam_s( name1, L_tmpnam_s );  
      if (err)  
      {  
         printf("Error occurred creating unique filename.\n");  
         exit(1);  
      }  
      else  
      {  
         printf( "%s is safe to use as a temporary file.\n", name1 );  
      }  
   }    
}  
```  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)