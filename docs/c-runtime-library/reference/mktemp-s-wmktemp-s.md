---
title: "_mktemp_s, _wmktemp_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_mktemp_s"
  - "_wmktemp_s"
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
  - "wmktemp_s"
  - "mktemp_s"
  - "_mktemp_s"
  - "_wmktemp_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_mktemp_s (función)"
  - "_tmktemp_s (función)"
  - "_wmktemp_s (función)"
  - "archivos [C++], temporal"
  - "mktemp_s (función)"
  - "archivos temporales [C++]"
  - "tmktemp_s (función)"
  - "wmktemp_s (función)"
ms.assetid: 92a7e269-7f3d-4c71-bad6-14bc827a451d
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# _mktemp_s, _wmktemp_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Crea un nombre único.  Estas versiones de [\_mktemp, \_wmktemp](../../c-runtime-library/reference/mktemp-wmktemp.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t _mktemp_s(  
   char *template,  
   size_t sizeInChars  
);  
errno_t _wmktemp_s(  
   wchar_t *template,  
   size_t sizeInChars  
);  
template <size_t size>  
errno_t _mktemp_s(  
   char (&template)[size]  
); // C++ only  
template <size_t size>  
errno_t _wmktemp_s(  
   wchar_t (&template)[size]  
); // C++ only  
```  
  
#### Parámetros  
 `template`  
 Perfil de nombre.  
  
 `sizeInChars`  
 Tamaño del búfer en caracteres de solo\- byte en `_mktemp_s`; caracteres anchos en `_wmktemp_s`, incluido el terminador nulo.  
  
## Valor devuelto  
 Devuelven cero de funciones en correctamente; un código de error del error.  
  
### Condiciones de error  
  
|`template`|`sizeInChars`|**valor devuelto**|**nuevo valor de plantilla**|  
|----------------|-------------------|------------------------|----------------------------------|  
|`NULL`|any|`EINVAL`|`NULL`|  
|Formato incorrecto \(vea la sección de `Remarks` para el formato correcto\)|any|`EINVAL`|cadena vacía|  
|any|\<\= número de X|`EINVAL`|cadena vacía|  
  
 Si es un de los sobre condiciones de error, el controlador no válido de parámetro se invoca, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, `errno` se establece en `EINVAL` y las funciones devuelven `EINVAL`.  
  
## Comentarios  
 La función de `_mktemp_s` crea un nombre de archivo único modificando el argumento de `template` , de modo que después de la llamada, los puntos del puntero de `template` en una cadena que contiene el nuevo nombre de archivo.  `_mktemp_s` controla automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos multibyte actualmente en uso por el sistema en tiempo de ejecución.  `_wmktemp_s` es una versión con caracteres anchos de `_mktemp_s`; el argumento de `_wmktemp_s` es una cadena de caracteres.  `_wmktemp_s` y `_mktemp_s` se comportan exactamente igual de otra forma, salvo que `_wmktemp_s` no controla las cadenas de multibyte\- carácter.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tmktemp_s`|`_mktemp_s`|`_mktemp_s`|`_wmktemp_s`|  
  
 El argumento de `template` tiene el formato `baseXXXXXX`, donde es la parte `base` del nuevo nombre de archivo que proporciona y cada X es un marcador de posición para un carácter proporcionado por `_mktemp_s`.  Cada carácter marcador en `template` debe ser mayúscula X.  `_mktemp_s` conserva `base` y reemplaza el primer X que se arrastra por un carácter alfabético.  `_mktemp_s` reemplaza X final siguiente con un valor de cinco dígitos; este valor es un número único que identifica el proceso de llamada, o en programas multiproceso, el subproceso de llamada.  
  
 Cada llamada correcta a `_mktemp_s` modifica `template`.  En cada llamada subsiguiente del mismo proceso o subproceso con el mismo argumento de `template` , las comprobaciones de `_mktemp_s` los nombres de archivo que coinciden con los nombres devueltos por `_mktemp_s` en llamadas anteriores.  Si ningún archivo existe para un nombre especificado, `_mktemp_s` devuelve ese nombre.  Si los archivos existen para todos los nombres previamente devueltos, `_mktemp_s` crea un nuevo nombre reemplazando el carácter alfabético que utilizó en el nombre previamente devuelto a minúscula disponible siguiente, en orden, de “a” a la “z”.  Por ejemplo, si es `base` :  
  
```  
fn  
```  
  
 y el valor de cinco dígitos proporcionado por `_mktemp_s` es 12345, el nombre devuelto es:  
  
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
  
 `_mktemp_s` pueden crear un máximo de 26 nombres de archivo únicos para cualquier combinación de valores de base y de la plantilla.  Por consiguiente, FNZ12345 es el nombre de archivo único pasado `_mktemp_s` puede crear por los valores de `base` y de `template` utilizados en este ejemplo.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_mktemp_s`|\<io.h\>|  
|`_wmktemp_s`|\<io.h o\> wchar.h \<\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_mktemp_s.cpp  
/* The program uses _mktemp to create  
 * five unique filenames. It opens each filename  
 * to ensure that the next name is unique.  
 */  
  
#include <io.h>  
#include <string.h>  
#include <stdio.h>  
  
char *fnTemplate = "fnXXXXXX";  
char names[5][9];  
  
int main()  
{  
   int i, err, sizeInChars;  
   FILE *fp;  
  
   for( i = 0; i < 5; i++ )  
   {  
      strcpy_s( names[i], sizeof(names[i]), fnTemplate );  
      /* Get the size of the string and add one for the null terminator.*/  
      sizeInChars = strnlen(names[i], 9) + 1;  
      /* Attempt to find a unique filename: */  
      err = _mktemp_s( names[i], sizeInChars );  
      if( err != 0 )  
         printf( "Problem creating the template" );  
      else  
      {  
         if( fopen_s( &fp, names[i], "w" ) == 0 )  
            printf( "Unique filename is %s\n", names[i] );  
         else  
            printf( "Cannot open %s\n", names[i] );  
         fclose( fp );  
      }  
   }  
  
   return 0;  
}  
```  
  
## Resultados del ejemplo  
  
```  
Unique filename is fna03188  
Unique filename is fnb03188  
Unique filename is fnc03188  
Unique filename is fnd03188  
Unique filename is fne03188  
```  
  
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
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)