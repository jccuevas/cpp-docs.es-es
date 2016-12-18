---
title: "_tempnam, _wtempnam, tmpnam, _wtmpnam | Microsoft Docs"
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
  - "_wtempnam"
  - "_wtmpnam"
  - "tmpnam"
  - "_tempnam"
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
  - "wtempnam"
  - "_wtmpnam"
  - "wtmpnam"
  - "tmpnam"
  - "_wtempnam"
  - "_tempnam"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tempnam (función)"
  - "_ttmpnam (función)"
  - "_wtempnam (función)"
  - "_wtmpnam (función)"
  - "nombres de archivo [C++], crear temporales"
  - "nombres de archivo [C++], temporal"
  - "tempnam (función)"
  - "archivos temporales, crear"
  - "tmpnam (función)"
  - "ttmpnam (función)"
  - "wtempnam (función)"
  - "wtmpnam (función)"
ms.assetid: 3ce75f0f-5e30-42a6-9791-8d7cbfe70fca
caps.latest.revision: 20
caps.handback.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _tempnam, _wtempnam, tmpnam, _wtmpnam
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genere los nombres que puede utilizar para crear los archivos temporales.  Hay disponibles versiones más seguras de algunas de estas funciones; vea [tmpnam\_s, \_wtmpnam\_s](../../c-runtime-library/reference/tmpnam-s-wtmpnam-s.md).  
  
## Sintaxis  
  
```  
char *_tempnam(  
   const char *dir,  
   const char *prefix   
);  
wchar_t *_wtempnam(  
   const wchar_t *dir,  
   const wchar_t *prefix   
);  
char *tmpnam(  
   char *str   
);  
wchar_t *_wtmpnam(  
   wchar_t *str   
);  
```  
  
#### Parámetros  
 `prefix`  
 La cadena que por los nombres devuelto por `_tempnam`.  
  
 `dir`  
 La ruta de acceso utilizada en el nombre de archivo si no hay ninguna variable de entorno TMP, o si TMP no es un directorio válido.  
  
 `str`  
 Puntero que contendrá el nombre generado y será idéntico al nombre devuelto por la función.  Ésta es una manera conveniente de guardar el nombre generado.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve un puntero al nombre generado o a `NULL` si hay un error.  El error puede producirse si intenta más que `TMP_MAX` \(vea STDIO.H\) las llamadas con `tmpnam` o si utiliza `_tempnam`y hay un nombre de directorio no válido especificado en la variable de entorno TMP y en el parámetro de `dir` .  
  
> [!NOTE]
>  Los punteros devueltos por `tmpnam` y el punto de `_wtmpnam` a los bufferes estáticos internos.  [libre](../../c-runtime-library/reference/free.md) no se debe llamar a para desasignar los punteros.  `free` necesita llamar para punteros asignados por `_tempnam` y `_wtempnam`.  
  
## Comentarios  
 Cada una de estas funciones devuelve el nombre de un archivo que no existe actualmente.  `tmpnam` devuelve un nombre único en el directorio de trabajo actual y `_tempnam` permite generar un nombre único en un directorio distinto del actual.  La nota a un nombre de archivo con por una barra diagonal inversa y ninguna información de la ruta de acceso, como \\fname21, esto indica que el nombre es válido para el directorio de trabajo actual.  
  
 Para `tmpnam`, puede almacenar este nombre de archivo generado en `str`.  Si `str` es `NULL`, después `tmpnam` deja el resultado en un buffer estático interno.  Para cualquier llamada subsiguiente destruye este valor.  El nombre generado por `tmpnam` consta de un nombre de archivo programa\- generado y, después de la primera llamada a `tmpnam`, una extensión de archivo números secuenciales en base 32 \(.1\-.vvu, cuando `TMP_MAX` en STDIO.H es 32.767\).  
  
 `_tempnam` generará un nombre único para un directorio elegido por las reglas siguientes:  
  
-   Si la variable de entorno TMP se define y se establece en un nombre de directorio válido, los nombres de archivo únicos se generarán para el directorio especificado por TMP.  
  
-   Si la variable de entorno TMP no se define o si se establece en el nombre de un directorio que no existe, `_tempnam` utilizará el parámetro de `dir` como la ruta que generará nombres únicos.  
  
-   Si la variable de entorno TMP no se define o si se establece en el nombre de un directorio que no existe, y si `dir` es `NULL` o establezca en nombre de un directorio que no existe, `_tempnam` utilizará el directorio de trabajo actual para generar nombres únicos.  Actualmente, si TMP y `dir` especifican los nombres de los directorios que no existen, la llamada a la función de `_tempnam` producirá un error.  
  
 El nombre devuelto por `_tempnam` será una concatenación de `prefix` y un número secuencial, que va a combinar para crear un nombre único para el directorio especificado.  `_tempnam` genera los nombres de archivo que no tienen ninguna extensión.  `_tempnam` utiliza [malloc](../../c-runtime-library/reference/malloc.md) para asignar espacio para el nombre de archivo; el programa es responsable de liberar este espacio cuando ya no se necesita.  
  
 `_tempnam` y `tmpnam` controlan automáticamente argumentos de cadena de multibyte\- carácter según corresponda, reconociendo secuencias de multibyte\- carácter según la página de códigos OEM obtenida del sistema operativo.  `_wtempnam` es una versión con caracteres anchos de `_tempnam`; los argumentos y el valor devuelto de `_wtempnam` son cadenas de caracteres.  `_wtempnam` y `_tempnam` se comportan exactamente igual excepto que `_wtempnam` no controla las cadenas de multibyte\- carácter.  `_wtmpnam` es una versión con caracteres anchos de `tmpnam`; el argumento y el valor devuelto de `_wtmpnam` son cadenas de caracteres anchos.  `_wtmpnam` y `tmpnam` se comportan exactamente igual excepto que `_wtmpnam` no controla las cadenas de multibyte\- carácter.  
  
 Si se definen `_DEBUG` y `_CRTDBG_MAP_ALLOC` , `_tempnam` y `_wtempnam` son reemplazados por llamadas a [\_tempnam\_dbg y \_wtempnam\_dbg](../../c-runtime-library/reference/tempnam-dbg-wtempnam-dbg.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ttmpnam`|`tmpnam`|`tmpnam`|`_wtmpnam`|  
|`_ttempnam`|`_tempnam`|`_tempnam`|`_wtempnam`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_tempnam`|\<stdio.h\>|  
|`_wtempnam`, `_wtmpnam`|\<stdio.h\> o \<wchar.h\>|  
|`tmpnam`|\<stdio.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_tempnam.c  
// compile with: /W3  
// This program uses tmpnam to create a unique filename in the  
// current working directory, then uses _tempnam to create   
// a unique filename with a prefix of stq.   
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{     
   char* name1 = NULL;  
   char* name2 = NULL;  
  
   // Create a temporary filename for the current working directory:   
   if( ( name1 = tmpnam( NULL ) ) != NULL ) // C4996  
   // Note: tmpnam is deprecated; consider using tmpnam_s instead  
      printf( "%s is safe to use as a temporary file.\n", name1 );  
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // Create a temporary filename in temporary directory with the  
   // prefix "stq". The actual destination directory may vary  
   // depending on the state of the TMP environment variable and  
   // the global variable P_tmpdir.     
  
   if( ( name2 = _tempnam( "c:\\tmp", "stq" ) ) != NULL )  
      printf( "%s is safe to use as a temporary file.\n", name2 );   
   else  
      printf( "Cannot create a unique filename\n" );  
  
   // When name2 is no longer needed :     
   if(name2)  
     free(name2);  
  
}  
```  
  
  **\\s1gk. es seguro de utilizar como archivo temporal.**  
**C:\\DOCUME~1\\user\\LOCALS~1\\Temp\\2\\stq2 es seguro de utilizar como archivo temporal.**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_getmbcp](../../c-runtime-library/reference/getmbcp.md)   
 [malloc](../../c-runtime-library/reference/malloc.md)   
 [\_setmbcp](../../c-runtime-library/reference/setmbcp.md)   
 [tmpfile](../../c-runtime-library/reference/tmpfile.md)   
 [tmpfile\_s](../../c-runtime-library/reference/tmpfile-s.md)