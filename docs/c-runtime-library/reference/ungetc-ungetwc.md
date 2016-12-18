---
title: "ungetc, ungetwc | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "ungetwc"
  - "ungetc"
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
  - "_ungettc"
  - "ungetwc"
  - "ungetc"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_ungettc (función)"
  - "caracteres, volver a insertar en secuencia"
  - "ungetc (función)"
  - "ungettc (función)"
  - "ungetwc (función)"
ms.assetid: e0754f3a-b4c6-408f-90c7-e6387b830d84
caps.latest.revision: 16
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ungetc, ungetwc
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Vuelve a insertar un carácter en el flujo.  
  
## Sintaxis  
  
```  
int ungetc(  
   int c,  
   FILE *stream   
);  
wint_t ungetwc(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### Parámetros  
 `c`  
 Carácter que se va a devolver.  
  
 `stream`  
 Puntero a la estructura `FILE`.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, cada una de estas funciones devuelve el argumento `c` *de carácter.* Si `c` no se puede volver a insertar o si no se ha leído ningún carácter, el flujo de entrada no cambia y `ungetc` devuelve `EOF`; `ungetwc` devuelve `WEOF`.  Si `stream` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, se devuelve `EOF` o `WEOF` y `errno` se establece en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `ungetc` vuelve a insertar el carácter `c` en `stream` y borra el indicador de fin de archivo.  El flujo debe estar abierto para lectura.  Una operación de lectura de `stream` subsiguiente empieza con `c`*.* Los intentos de insertar `EOF` en el flujo mediante `ungetc` se omiten.  
  
 Los caracteres que `ungetc` pone en el flujo se podrían borrar si se llama a `fflush`, `fseek`, `fsetpos` o `rewind` antes de que se lea el carácter del flujo.  El indicador de posición de archivo tendrá el valor que tenía antes de que se volvieran a insertar los caracteres.  El almacenamiento externo correspondiente al flujo no cambia.  Si una llamada de `ungetc` en un flujo de texto se realiza correctamente, el indicador de posición del archivo está sin especificar hasta que se leen o se descarten todos los caracteres que se han vuelto a insertar.  En cada llamada correcta de `ungetc` en un flujo binario se reduce el indicador de posición de archivo. Si el valor era 0 antes de una llamada, el valor queda sin definir después de la llamada.  
  
 Los resultados son imprevisibles si se llama a `ungetc` dos veces sin que haya una operación de lectura o de posición de archivo entre las dos llamadas.  Después de una llamada a `fscanf`, una llamada a `ungetc` puede generar un error a menos que se haya realizado otra operación de lectura \(por ejemplo `getc`\).  La razón es que la función `fscanf` ya llama a `ungetc`.  
  
 `ungetwc` es una versión con caracteres anchos de `ungetc`.  Sin embargo, en cada llamada correcta de `ungetwc` en un flujo de texto o binario, el valor del indicador de posición de archivo no se especifica hasta que se leen o se descartan todos los caracteres que se han vuelto a insertar.  
  
 Estas funciones son seguras para subprocesos y bloquean los datos confidenciales durante la ejecución.  Para consultar una versión que no realiza el bloqueo, vea [\_ungetc\_nolock, \_ungetwc\_nolock](../../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ungettc`|`ungetc`|`ungetc`|`ungetwc`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`ungetc`|\<stdio.h\>|  
|`ungetwc`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_ungetc.c  
// This program first converts a character  
// representation of an unsigned integer to an integer. If  
// the program encounters a character that is not a digit,  
// the program uses ungetc to replace it in the  stream.  
//  
  
#include <stdio.h>  
#include <ctype.h>  
  
int main( void )  
{  
   int ch;  
   int result = 0;  
  
   // Read in and convert number:  
   while( ((ch = getchar()) != EOF) && isdigit( ch ) )  
      result = result * 10 + ch - '0';    // Use digit.  
   if( ch != EOF )  
      ungetc( ch, stdin );                // Put nondigit back.  
   printf( "Number = %d\nNext character in stream = '%c'",   
            result, getchar() );  
}  
```  
  
  **`521a`Número \= 521**  
**Siguiente carácter del flujo \= 'a'**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [getc, getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc, putwc](../../c-runtime-library/reference/putc-putwc.md)