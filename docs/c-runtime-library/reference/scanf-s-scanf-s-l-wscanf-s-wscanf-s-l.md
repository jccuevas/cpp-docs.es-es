---
title: "scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l | Microsoft Docs"
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
  - "wscanf_s"
  - "_wscanf_s_l"
  - "scanf_s"
  - "_scanf_s_l"
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
  - "wscanf_s"
  - "_tscanf_s_l"
  - "_wscanf_s_l"
  - "scanf_s"
  - "_tscanf_s"
  - "_scanf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "leer datos [C++], en secuencias de entrada"
  - "búferes [C++], saturaciones del búfer"
  - "_scanf_s_l (función)"
  - "_wscanf_s_l (función)"
  - "tscanf_s_l (función)"
  - "tscanf_s (función)"
  - "scanf_s (función)"
  - "lectura del flujo de entrada de datos [C++]"
  - "wscanf_s (función)"
  - "_tscanf_s_l (función)"
  - "_tscanf_s (función)"
  - "scanf_s_l (función)"
  - "datos con formato [C++], en secuencias de entrada"
  - "wscanf_s_l (función)"
  - "búferes [C++], evitar saturaciones"
ms.assetid: 42cafcf7-52d6-404a-80e4-b056a7faf2e5
caps.latest.revision: 33
caps.handback.revision: 33
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato del flujo de entrada estándar. Estas versiones de [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int scanf_s(  
   const char *format [,  
   argument]...   
);  
int _scanf_s_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wscanf_s(  
   const wchar_t *format [,  
   argument]...   
);  
int _wscanf_s_l(  
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
 Devuelve el número de campos que se han convertido y asignado correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es `EOF` para un error, o si se encuentra el carácter de final de archivo o el carácter de final de cadena en el primer intento de leer un carácter. Si `format` es un `NULL` se invoca el puntero, el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `scanf_s` y `wscanf_s` devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `scanf_s` lee datos del flujo de entrada estándar `stdin` y escribe los datos en la ubicación que se proporciona en `argument`. Cada `argument` debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
 `wscanf_s` es una versión con caracteres anchos de `scanf_s`; el argumento `format` para `wscanf_s` es una cadena de caracteres anchos.`wscanf_s` y `scanf_s` se comportan exactamente igual si el flujo se abre en modo ANSI.`scanf_s` no admite actualmente la entrada desde un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.  
  
 A diferencia de `scanf` y `wscanf`, `scanf_s` y `wscanf_s` requieren que se especifique el tamaño de búfer para todos los parámetros de entrada del tipo `c`, `C`, `s`, `S`, o los conjuntos de control de cadenas que se incluyen en `[]`. El tamaño de búfer en caracteres se pasa como parámetro adicional inmediatamente después del puntero en el búfer o la variable. Por ejemplo, si está leyendo una cadena, el tamaño de búfer para esa cadena se pasa como se indica a continuación:  
  
 `char s[10];`  
  
 `scanf_s("%9s", s, (unsigned)_countof(s)); // buffer size is 10, width specification is 9`  
  
 El tamaño de búfer incluye el valor nulo final. Puede usar un campo de especificación de ancho para garantizar que el token que se lee se ajustará al búfer. Si no se usa ningún campo de especificación de ancho y la lectura de token es demasiado grande como para ajustarse al búfer, no se escribirá ningún valor en dicho búfer.  
  
> [!NOTE]
>  El parámetro de tamaño es del tipo `unsigned`, no `size_t`. Utilice una conversión de tipos estática para convertir un `size_t` valor `unsigned` configuraciones de compilación de 64 bits.  
  
 En el ejemplo siguiente se muestra que el parámetro de tamaño de búfer indica el número máximo de caracteres, no bytes. En la llamada a `wscanf_s`, el ancho de caracteres que se indica mediante el tipo de búfer no coincide con el ancho de caracteres que se indica mediante el especificador de formato.  
  
```  
wchar_t ws[10];  
wscanf_s(L"%9S", ws, (unsigned)_countof(ws));  
```  
  
 El especificador de formato `S` indica el uso del ancho de carácter que es “opuesto” al ancho predeterminado admitido por la función. El ancho de carácter es de un solo byte, pero la función admite caracteres de doble byte. En este ejemplo se lee una cadena de hasta 9 caracteres con ancho de un solo byte y los coloca en un búfer de caracteres con ancho de doble byte. Los caracteres se tratan como valores de un solo byte; los primeros dos caracteres se almacenan en `ws[0]`, los siguientes dos se almacenan en `ws[1]`, y así sucesivamente.  
  
 En el caso de los caracteres, un carácter individual puede leerse como se indica a continuación:  
  
 `char c;`  
  
 `scanf_s("%c", &c, 1);`  
  
 Cuando se leen varios caracteres para cadenas que no tienen un valor nulo final, se usan enteros como especificación del ancho y el tamaño de búfer.  
  
 `char c[4];`  
  
 `scanf_s("%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 Para obtener más información, consulta [scanf \(Especificación de ancho\)](../../c-runtime-library/scanf-width-specification.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tscanf_s`|`scanf_s`|`scanf_s`|`wscanf_s`|  
|`_tscanf_s_l`|`_scanf_s_l`|`_scanf_s_l`|`_wscanf_s_l`|  
  
 Para obtener más información, consulta [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`scanf_s`, `_scanf_s_l`|\<stdio.h\>|  
|`wscanf_s`, `_wscanf_s_l`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_scanf_s.c  
// This program uses the scanf_s and wscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int      i,  
            result;  
   float    fp;  
   char     c,  
            s[80];  
   wchar_t  wc,  
            ws[80];  
  
   result = scanf_s( "%d %f %c %C %s %S", &i, &fp, &c, 1,  
                     &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );  
   printf( "The number of fields input is %d\n", result );  
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c,  
           wc, s, ws);  
   result = wscanf_s( L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                      &wc, 1, s, (unsigned)_countof(s), ws, (unsigned)_countof(ws) );  
   wprintf( L"The number of fields input is %d\n", result );  
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp,  
            c, wc, s, ws);  
}  
```  
  
 Este programa produce el siguiente resultado cuando se especifica esta entrada:  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
```Output  
El número de entrada de los campos es 6, el contenido: el número de campos de entrada de caracteres de Byte 71 z de 98.599998 h es 6, el contenido es: caracteres anchos 36 92.300003 y n  
```  
  
## Equivalente en .NET Framework  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   Consulte también `Parse` métodos, como [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)