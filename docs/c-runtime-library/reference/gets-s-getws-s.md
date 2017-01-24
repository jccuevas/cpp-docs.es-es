---
title: "gets_s, _getws_s | Microsoft Docs"
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
  - "_getws_s"
  - "gets_s"
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
  - "_getws_s"
  - "gets_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getws_s (función)"
  - "desbordamientos del búfer"
  - "búferes, evitar desbordamientos"
  - "búferes, desbordamientos del búfer"
  - "gets_s (función)"
  - "getws_s (función)"
  - "líneas, obtener"
  - "entrada estándar, leer"
  - "secuencias, obtener líneas"
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gets_s, _getws_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene una línea del flujo `stdin`.  Estas versiones de [gets, \_getws](../../c-runtime-library/gets-getws.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
char *gets_s(   
   char *buffer,  
   size_t sizeInCharacters  
);  
wchar_t *_getws_s(   
   wchar_t *buffer,  
   size_t sizeInCharacters  
);  
template <size_t size>  
char *gets_s(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws_s(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### Parámetros  
 \[out\] `buffer`  
 Ubicación de almacenamiento de la cadena de entrada.  
  
 \[in\] `sizeInCharacters`  
 Tamaño del búfer.  
  
## Valor devuelto  
 Si la operación se realiza correctamente, devuelve `buffer`.  Un puntero `NULL` indica un error o una condición de fin de archivo.  Utilice [ferror](../../c-runtime-library/reference/ferror.md) o [feof](../../c-runtime-library/reference/feof.md) para determinar qué resultado se ha producido.  
  
## Comentarios  
 La función `gets_s` lee una línea del flujo de entrada estándar `stdin` y la almacena en `buffer`.  La línea consta de todos los caracteres hasta el primer carácter de línea nueva \('\\n'\), este último incluido.  A continuación, `gets_s` reemplaza el carácter de línea nueva con un carácter nulo \('\\0'\) antes de devolver la línea.  Por su parte, la función `fgets_s` conserva el carácter de línea nueva.  
  
 Si el primer carácter que se lee es el carácter de final de archivo, se almacena un carácter nulo al principio de `buffer` y se devuelve `NULL`.  
  
 `_getws` es una versión con caracteres anchos de `gets_s`; el argumento y el valor devuelto son cadenas de caracteres anchos.  
  
 Si `buffer` es `NULL` o `sizeInCharacters` es menor o igual que cero, o si el búfer es demasiado pequeño para contener la línea de entrada y el terminador nulo, estas funciones invocan el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `NULL` y establecen errno en `ERANGE`.  
  
 En C\+\+, el uso de estas funciones se simplifica con las sobrecargas de plantilla; las sobrecargas pueden realizar una inferencia automáticamente de la longitud de búfer \(lo que elimina la necesidad de especificar un argumento de tamaño\) y pueden reemplazar automáticamente funciones anteriores no seguras con sus homólogos seguros más recientes.  Para obtener más información, vea [Sobrecargas de plantilla seguras](../../c-runtime-library/secure-template-overloads.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_getts`|`gets_s`|`gets_s`|`_getws`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`gets_s`|\<stdio.h\>|  
|`_getws`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_gets_s.c  
// This program retrieves a string from the stdin and   
// prints the same string to the console.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets_s( line, 20 );  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
  **`¡Hola allí!` La línea que se especificó fue: Hello there\!**   
## Equivalente en .NET Framework  
 [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [gets, \_getws](../../c-runtime-library/gets-getws.md)   
 [fgets, fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs, fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [puts, \_putws](../../c-runtime-library/reference/puts-putws.md)