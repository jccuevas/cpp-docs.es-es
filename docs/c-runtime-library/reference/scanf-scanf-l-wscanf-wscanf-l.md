---
title: "scanf, _scanf_l, wscanf, _wscanf_l | Microsoft Docs"
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
  - "_wscanf_l"
  - "scanf"
  - "_scanf_l"
  - "wscanf"
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
  - "_tscanf"
  - "_scanf_l"
  - "wscanf"
  - "_wscanf_l"
  - "scanf"
  - "_tscanf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_scanf_l (función)"
  - "_tscanf (función)"
  - "_tscanf_l (función)"
  - "_wscanf_l (función)"
  - "datos [C++], leer en secuencia de entrada"
  - "datos con formato [C++], en secuencias de entrada"
  - "leer datos [C++], en secuencias de entrada"
  - "scanf (función)"
  - "scanf_l (función)"
  - "tscanf (función)"
  - "tscanf_l (función)"
  - "wscanf (función)"
  - "wscanf_l (función)"
ms.assetid: 73eac607-117f-4be4-9ff0-4afd9cf3c848
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scanf, _scanf_l, wscanf, _wscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato del flujo de entrada estándar.  Hay disponibles versiones más seguras de estas funciones; vea [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md).  
  
## Sintaxis  
  
```  
int scanf(  
   const char *format [,  
   argument]...   
);  
int _scanf_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wscanf(  
   const wchar_t *format [,  
   argument]...   
);  
int _wscanf_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### Parámetros  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve el número de campos que se han convertido y asignado correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  
  
 Si `format` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `scanf` lee datos del flujo de entrada estándar `stdin` y escribe los datos en la ubicación que se proporciona en `argument`.  Cada `argument` debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Al leer una cadena con `scanf`, especifique siempre un ancho para el formato `%s` \(por ejemplo, `"%32s"` en lugar de `"%s"`\); si no se hace así, el formato incorrecto de la entrada puede provocar una saturación del búfer.  También puede usar [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) o [fgets](../../c-runtime-library/reference/fgets-fgetws.md).  
  
 `wscanf` es una versión con caracteres anchos de `scanf`; el argumento `format` para `wscanf` es una cadena de caracteres anchos.  `wscanf` y `scanf` se comportan exactamente igual si el flujo se abre en modo ANSI.  `scanf` no admite actualmente la entrada desde un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tscanf`|`scanf`|`scanf`|`wscanf`|  
|`_tscanf_l`|`_scanf_l`|`_scanf_l`|`_wscanf_l`|  
  
 Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`scanf`, `_scanf_l`|\<stdio.h\>|  
|`wscanf`, `_wscanf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_scanf.c  
// compile with: /W3  
 /* This program uses the scanf and wscanf functions  
  * to read formatted input.  
  */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int   i, result;  
   float fp;  
   char  c, s[81];  
   wchar_t wc, ws[81];  
   result = scanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws ); // C4996  
   // Note: scanf and wscanf are deprecated; consider using scanf_s and wscanf_s  
   printf( "The number of fields input is %d\n", result );  
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
   result = wscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws ); // C4996  
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