---
title: "_mktemp, _wmktemp | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wmktemp"
  - "_mktemp"
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
  - "_tmktemp"
  - "wmktemp"
  - "tmktemp"
  - "_wmktemp"
  - "_mktemp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mktemp (función)"
  - "_tmktemp (función)"
  - "_wmktemp (función)"
  - "archivos [C++], temporal"
  - "mktemp (función)"
  - "archivos temporales [C++]"
  - "tmktemp (función)"
  - "wmktemp (función)"
ms.assetid: 055eb539-a8c2-4a7d-be54-f5b6d1eb5c85
caps.latest.revision: 25
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 25
---
# _mktemp, _wmktemp
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un nombre único.  Hay disponibles versiones más seguras de estas funciones; vea [\_mktemp\_s, \_wmktemp\_s](../../c-runtime-library/reference/mktemp-s-wmktemp-s.md).  
  
## Sintaxis  
  
```  
char *_mktemp(  
   char *template   
);  
wchar_t *_wmktemp(  
   wchar_t *template   
);  
template <size_t size>  
char *_mktemp(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_wmktemp(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### Parámetros  
 `template`  
 Perfil de nombre.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero a la plantilla modificada.  La función devuelve `NULL` si `template` se forma mal o no más de nombres únicos se pueden crear de plantilla especificada.  
  
## Comentarios  
 La función de `_mktemp` crea un nombre de archivo único modificando el argumento de `template` .  `_mktemp` controla automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos multibyte actualmente en uso por el sistema en tiempo de ejecución.  `_wmktemp` es una versión con caracteres anchos de `_mktemp`; el argumento y el valor devuelto de `_wmktemp` son cadenas de caracteres anchos.  `_wmktemp` y `_mktemp` se comportan exactamente igual de otra forma, salvo que `_wmktemp` no controla las cadenas de multibyte\- carácter.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tmktemp`|`_mktemp`|`_mktemp`|`_wmktemp`|  
  
 El argumento de `template` tiene el formato `base`XXXXXX, donde es la parte `base` del nuevo nombre de archivo que proporciona y cada X es un marcador de posición para un carácter proporcionado por `_mktemp`.  Cada carácter marcador en `template` debe ser mayúscula X.  `_mktemp` conserva `base` y reemplaza el primer X que se arrastra por un carácter alfabético.  `_mktemp` reemplaza X final siguiente con un valor de cinco dígitos; este valor es un número único que identifica el proceso de llamada, o en programas multiproceso, el subproceso de llamada.  
  
 Cada llamada correcta a `_mktemp` modifica `template`.  En cada llamada subsiguiente del mismo proceso o subproceso con el mismo argumento de `template` , las comprobaciones de `_mktemp` los nombres de archivo que coinciden con los nombres devueltos por `_mktemp` en llamadas anteriores.  Si ningún archivo existe para un nombre especificado, `_mktemp` devuelve ese nombre.  Si los archivos existen para todos los nombres previamente devueltos, `_mktemp` crea un nuevo nombre reemplazando el carácter alfabético que utilizó en el nombre previamente devuelto a minúscula disponible siguiente, en orden, de “a” a la “z”.  Por ejemplo, si es `base` :  
  
```  
fn  
```  
  
 y el valor de cinco dígitos proporcionado por `_mktemp` es 12345, el nombre devuelto es:  
  
```  
fna12345  
```  
  
 Si este nombre se utiliza para crear el archivo FNA12345 y todavía existe este archivo, el siguiente nombre devuelto en una llamada el mismo proceso o subproceso con el mismo `base` para `template` es:  
  
```  
fnb12345  
```  
  
 Si no existe FNA12345, el siguiente nombre devuelto está de nuevo:  
  
```  
fna12345  
```  
  
 `_mktemp` pueden crear un máximo de 26 nombres de archivo únicos para cualquier combinación de valores de base y de la plantilla.  Por consiguiente, FNZ12345 es el nombre de archivo único pasado `_mktemp` puede crear por los valores de `base` y de `template` utilizados en este ejemplo.  
  
 En el error, se establece `errno` .  Si `template` tiene un formato no válido \(por ejemplo, menos de 6 X\), `errno` se establece en `EINVAL`.  Si `_mktemp` no puede crear un nombre único porque existen los 26 nombres de archivo posibles ya, `_mktemp` establece la plantilla en una cadena vacía y devuelve `EEXIST`.  
  
 En C\+\+, estas funciones tienen sobrecargas de plantilla que invocan los homólogos seguros más recientes de estas funciones.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mktemp`|\<io.h\>|  
|`_wmktemp`|\<io.h o\> wchar.h \<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_mktemp.c  
// compile with: /W3  
/* The program uses _mktemp to create  
 * unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
#include <errno.h>  
  
char *template = "fnXXXXXX";  
char *result;  
char names[27][9];  
  
int main( void )  
{  
   int i;  
   FILE *fp;  
  
   for( i = 0; i < 27; i++ )  
   {  
      strcpy_s( names[i], sizeof( names[i] ), template );  
      /* Attempt to find a unique filename: */  
      result = _mktemp( names[i] );  // C4996  
      // Note: _mktemp is deprecated; consider using _mktemp_s instead  
      if( result == NULL )  
      {  
         printf( "Problem creating the template\n" );  
         if (errno == EINVAL)  
         {  
             printf( "Bad parameter\n");  
         }  
         else if (errno == EEXIST)  
         {  
             printf( "Out of unique filenames\n");   
         }  
      }  
      else  
      {  
         fopen_s( &fp, result, "w" );  
         if( fp != NULL )  
            printf( "Unique filename is %s\n", result );  
         else  
            printf( "Cannot open %s\n", result );  
         fclose( fp );  
      }  
   }  
}  
```  
  
  **El nombre de archivo único es fna03912**  
**El nombre de archivo único es fnb03912**  
**El nombre de archivo único es fnc03912**  
**El nombre de archivo único es fnd03912**  
**El nombre de archivo único es fne03912**  
**El nombre de archivo único es fnf03912**  
**El nombre de archivo único es fng03912**  
**El nombre de archivo único es fnh03912**  
**El nombre de archivo único es fni03912**  
**El nombre de archivo único es fnj03912**  
**El nombre de archivo único es fnk03912**  
**El nombre de archivo único es fnl03912**  
**El nombre de archivo único es fnm03912**  
**El nombre de archivo único es fnn03912**  
**El nombre de archivo único es fno03912**  
**El nombre de archivo único es fnp03912**  
**El nombre de archivo único es fnq03912**  
**El nombre de archivo único es fnr03912**  
**El nombre de archivo único es fns03912**  
**El nombre de archivo único es fnt03912**  
**El nombre de archivo único es fnu03912**  
**El nombre de archivo único es fnv03912**  
**El nombre de archivo único es fnw03912**  
**El nombre de archivo único es fnx03912**  
**El nombre de archivo único es fny03912**  
**El nombre de archivo único es fnz03912**  
**Problema que crea la plantilla.**  
**Fuera de nombres de archivo únicos.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Control de archivos](../../c-runtime-library/file-handling.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [\_getpid](../../c-runtime-library/reference/getpid.md)   
 [\_open, \_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [\_tempnam, \_wtempnam, tmpnam, \_wtmpnam](../../c-runtime-library/reference/tempnam-wtempnam-tmpnam-wtmpnam.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)