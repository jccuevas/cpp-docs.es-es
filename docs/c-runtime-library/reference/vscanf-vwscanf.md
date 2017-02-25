---
title: "vscanf, vwscanf | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vscanf"
  - "vwscanf"
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
  - "vscanf"
  - "vwscanf"
  - "_vtscanf"
dev_langs: 
  - "C++"
ms.assetid: d1df595b-11bc-4682-9441-a92616301e3b
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# vscanf, vwscanf
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato del flujo de entrada estándar.  Hay disponibles versiones más seguras de estas funciones; vea [vscanf\_s, vwscanf\_s](../../c-runtime-library/reference/vscanf-s-vwscanf-s.md).  
  
## Sintaxis  
  
```  
int vscanf(  
   const char *format,  
   va_list arglist  
);  
int vwscanf(  
   const wchar_t *format,  
   va_list arglist  
);  
  
```  
  
#### Parámetros  
 `format`  
 Cadena de control de formato.  
  
 `arglist`  
 Lista de argumentos de variable.  
  
## Valor devuelto  
 Devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  
  
 Si `format` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `vscanf` lee datos de la secuencia de entrada estándar `stdin` y escribe los datos en ubicaciones que se proporcionan por la lista de argumentos `arglist`.  Cada argumento de la lista debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Cuando se utiliza `vscanf` para leer una cadena, especifique siempre un ancho para el formato `%s` \(por ejemplo, `"%32s"` en lugar de `"%s"`\); si no, el formato incorrecto de la entrada puede provocar una saturación del búfer.  Como alternativa, puede usar la propiedad [vscanf\_s, vwscanf\_s](../../c-runtime-library/reference/vscanf-s-vwscanf-s.md) o [fgets](../../c-runtime-library/reference/fgets-fgetws.md).  
  
 `vwscanf` es una versión con caracteres anchos de `vscanf`; el argumento `format` para `vwscanf` es una cadena de caracteres anchos.  `vwscanf` y `vscanf` se comportan exactamente igual si el flujo se abre en modo ANSI.  `vscanf` no admite la entrada desde una secuencia de UNICODE.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vtscanf`|`vscanf`|`vscanf`|`vwscanf`|  
  
 Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`vscanf`|\<stdio.h\>|  
|`vwscanf`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_vscanf.c  
// compile with: /W3  
// This program uses the vscanf and vwscanf functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
int call_vscanf(char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vscanf(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int call_vwscanf(wchar_t *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vwscanf(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    int   i, result;  
    float fp;  
    char  c, s[81];  
    wchar_t wc, ws[81];  
    result = call_vscanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws );  
    printf( "The number of fields input is %d\n", result );  
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
    result = call_vwscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws );  
    wprintf( L"The number of fields input is %d\n", result );  
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);  
}  
  
```  
  
  **`Caracteres de byte 71 98.6 h z Caracteres anchos 36 92.3 y n`El número de la entrada de los campos es 6**  
**El contenido es: Caracteres de byte 71 98.599998 h z**  
**El número de entrada de campos es 6**  
**El contenido es: Caracteres anchos 36 92.300003 y n**   
## Equivalente en .NET Framework  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   Vea también los métodos `Parse`, como [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vscanf\_s, vwscanf\_s](../../c-runtime-library/reference/vscanf-s-vwscanf-s.md)