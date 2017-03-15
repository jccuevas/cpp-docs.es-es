---
title: "printf, _printf_l, wprintf, _wprintf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_printf_l"
  - "wprintf"
  - "_wprintf_l"
  - "printf"
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
  - "printf"
  - "_tprintf"
  - "wprintf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_printf_l (función)"
  - "_tprintf (función)"
  - "_tprintf_l (función)"
  - "_wprintf_l (función)"
  - "texto con formato [C++]"
  - "printf (función)"
  - "printf (función), especificación de formato (campos)"
  - "printf (función), utilizar"
  - "printf_l (función)"
  - "tprintf (función)"
  - "tprintf_l (función)"
  - "wprintf (función)"
  - "wprintf_l (función)"
  - "escribir en consola"
ms.assetid: 77a854ae-5b48-4865-89f4-f2dc5cf80f52
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# printf, _printf_l, wprintf, _wprintf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Imprime el resultado con formato en la cadena de salida estándar.  Hay disponibles versiones más seguras de estas funciones; vea [printf\_s, \_printf\_s\_l, wprintf\_s, \_wprintf\_s\_l](../../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md).  
  
## Sintaxis  
  
```  
int printf(  
   const char *format [,  
   argument]...   
);  
int _printf_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wprintf(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### Parámetros  
 `format`  
 Control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Devuelve el número de caracteres impreso o un valor negativo si se produce un error.  Si `format` es `NULL`, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve \-1 y establece `errno` en `EINVAL`.  Si **EOF** \(0xFFFF\) se encuentra en `argument`, la función devuelve \-1.  
  
 Para obtener información sobre `errno` y códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `printf` da formato e imprime una serie de caracteres y valores en el flujo de salida estándar, `stdout`.  Si los argumentos siguen a la cadena de `format`, la cadena de `format` debe contener las especificaciones que determinan el formato de salida de los argumentos.  `printf` y [fprintf](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md) se comportan exactamente igual excepto que `printf` escribe salida a `stdout` y no a un destino de tipo `FILE`.  
  
 `wprintf` es una versión con caracteres anchos de `printf`; `format` es una cadena de caracteres anchos.  `wprintf` y `printf` se comportan exactamente igual si el flujo se abre en modo ANSI.  `printf` no admite actualmente la salida a un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_unicode definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tprintf`|`printf`|`printf`|`wprintf`|  
  
 El argumento `format` consta de caracteres ordinarios, secuencias de escape y \(si los argumentos siguen `format`\) especificaciones de formato.  Los caracteres y las secuencias de escape ordinarios se copian en `stdout` en orden de aparición.  Por ejemplo, la línea:  
  
```  
printf("Line one\n\t\tLine two\n");   
```  
  
 genera el resultado:  
  
```  
Line one  
        Line two  
```  
  
 Las [especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md) siempre comienzan con un signo de porcentaje \(`%`\) y se leen de izquierda a derecha.  Cuando `printf` encuentra la primera especificación de formato \(si existe\), convierte el valor del primer argumento después de `format` y lo representa en consecuencia.  La segunda especificación de formato genera el segundo argumento que se convertirá y saldrá, y así sucesivamente.  Si hay más argumentos que especificaciones de formato, se omiten los argumentos adicionales.  Los resultados son indefinidos si no hay suficientes argumentos para todas las especificaciones de formato.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tprintf`|`printf`|`printf`|`wprintf`|  
|`_tprintf_l`|`_printf_l`|`_printf_l`|`_wprintf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`printf`, `_printf_l`|\<stdio.h\>|  
|`wprintf`, `_wprintf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)].  Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_printf.c  
// This program uses the printf and wprintf functions  
// to produce formatted output.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char     ch = 'h',   
            *string = "computer";  
   wchar_t  wch = L'w',   
            *wstring = L"Unicode";  
   int      count = -9234;  
   double   fp = 251.7366;  
  
   // Display integers  
   printf( "Integer formats:\n"  
           "   Decimal: %d  Justified: %.6d  "  
           "Unsigned: %u\n",  
           count, count, count, count );  
  
   // Display decimals  
   printf( "Decimal %d as:\n   Hex: %Xh  "  
           "C hex: 0x%x  Octal: %o\n",  
            count, count, count, count );  
  
   // Display in different radixes  
   printf( "Digits 10 equal:\n   Hex: %i  "  
           "Octal: %i  Decimal: %i\n",  
            0x10, 010, 10 );  
  
   // Display characters  
   printf("Characters in field (1):\n"  
          "%10c%5hc%5C%5lc\n",  
          ch, ch, wch, wch);  
   wprintf(L"Characters in field (2):\n"  
           L"%10C%5hc%5c%5lc\n",  
           ch, ch, wch, wch);  
  
   // Display strings  
   printf("Strings in field (1):\n%25s\n"  
          "%25.4hs\n   %S%25.3ls\n",  
          string, string, wstring, wstring);  
   wprintf(L"Strings in field (2):\n%25S\n"  
           L"%25.4hs\n   %s%25.3ls\n",  
           string, string, wstring, wstring);  
  
   // Display real numbers  
   printf("Real numbers:\n   %f %.2f %e %E\n",  
          fp, fp, fp, fp );  
  
   // Display pointer  
   printf( "\nAddress as:   %p\n", &count);  
}  
```  
  
## Resultados del ejemplo  
  
```  
Integer formats:  
   Decimal: -9234  Justified: -009234  Unsigned: 4294958062  
Decimal -9234 as:  
   Hex: FFFFDBEEh  C hex: 0xffffdbee  Octal: 37777755756  
Digits 10 equal:  
   Hex: 16  Octal: 8  Decimal: 10  
Characters in field (1):  
         h    h    w    w  
Characters in field (2):  
         h    h    w    w  
Strings in field (1):  
                 computer  
                     comp  
   Unicode                      Uni  
Strings in field (2):  
                 computer  
                     comp  
   Unicode                      Uni  
Real numbers:  
   251.736600 251.74 2.517366e+002 2.517366E+002  
  
Address as:   0012FF3C  
```  
  
## Equivalente en .NET Framework  
  
-   [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
-   [System::Console::WriteLine](https://msdn.microsoft.com/en-us/library/system.console.writeline.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [fopen, \_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_fprintf\_p, \_fprintf\_p\_l, \_fwprintf\_p, \_fwprintf\_p\_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vprintf \(Funciones\)](../../c-runtime-library/vprintf-functions.md)   
 [\_set\_output\_format](../../c-runtime-library/set-output-format.md)