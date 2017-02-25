---
title: "_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_fwprintf_p"
  - "_fprintf_p_l"
  - "_fwprintf_p_l"
  - "_fprintf_p"
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
  - "_fprintf_p"
  - "_ftprintf_p"
  - "fwprintf_p"
  - "_fwprintf_p"
  - "fprintf_p"
  - "ftprintf_p"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_fprintf_p (función)"
  - "_fprintf_p_l (función)"
  - "_ftprintf_p (función)"
  - "_ftprintf_p_l (función)"
  - "_fwprintf_p (función)"
  - "_fwprintf_p_l (función)"
  - "fprintf_p (función)"
  - "fprintf_p_l (función)"
  - "ftprintf_p (función)"
  - "ftprintf_p_l (función)"
  - "fwprintf_p (función)"
  - "fwprintf_p_l (función)"
  - "imprimir [C++], datos con formato en secuencias"
  - "secuencias, imprimir datos con formato en"
ms.assetid: 46b082e1-45ba-4383-9ee4-97015aa50bc6
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Imprime datos con formato en una secuencia.  
  
## Sintaxis  
  
```  
int _fprintf_p(   
   FILE *stream,  
   const char *format [,  
   argument ]...  
);  
int _fprintf_p_l(   
   FILE *stream,  
   const char *format,  
   locale_t locale [,  
   argument ]...  
);  
int _fwprintf_p(   
   FILE *stream,  
   const wchar_t *format [,  
   argument ]...  
);  
int _fwprintf_p_l(   
   FILE *stream,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ]...  
);  
```  
  
#### Parámetros  
 `stream`  
 Puntero a la estructura de `FILE`.  
  
 `format`  
 Cadena de control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_fprintf_p` y `_fwprintf_p` devuelven el número de caracteres de escribir o devuelven un valor negativo cuando un error de salida aparece.  
  
## Comentarios  
 `_fprintf_p` da formato y imprime una serie de caracteres y valores al resultado `stream`.  Cada función `argument` \(si existe\) se convierte y salida según la especificación correspondiente de formato en `format`.  Para `_fprintf_p`, el argumento de `format` tiene la misma sintaxis y uso que tiene en `_printf_p`.  Estas funciones admiten parámetros posicionales, lo que significa que el orden de los parámetros utilizados por la cadena de formato se puede cambiar.  Para obtener más información sobre parámetros posicionales, vea [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_fwprintf_p` es una versión con caracteres anchos de `_fprintf_p`; en `_fwprintf_p`, `format` es una cadena de caracteres.  Estas funciones se comportan igual si el flujo se abre en modo ANSI.  `_fprintf_p` no admite actualmente la salida en un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
 Como las versiones de no Secure \(vea [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)\), estas funciones validan sus parámetros y se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md), si `stream` o `format` es un puntero NULL o si hay algún desconocido o formado mal dando formato especificadores.  Si la ejecución puede continuar, las funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_ftprintf_p`|`_fprintf_p`|`_fprintf_p`|`_fwprintf_p`|  
|`_ftprintf_p_l`|`_fprintf_p_l`|`_fprintf_p_l`|`_fwprintf_p_l`|  
  
 Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
## Requisitos  
  
|Función|Encabezado necesario|  
|-------------|--------------------------|  
|`_fprintf_p`, `_fprintf_p_l`|\<stdio.h\>|  
|`_fwprintf_p`, `_fwprintf_p_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_fprintf_p.c  
// This program uses _fprintf_p to format various  
// data and print it to the file named FPRINTF_P.OUT. It  
// then displays FPRINTF_P.OUT on the screen using the system  
// function to invoke the operating-system TYPE command.  
//   
  
#include <stdio.h>  
#include <process.h>  
  
int main( void )  
{  
    FILE    *stream = NULL;  
    int     i = 10;  
    double  fp = 1.5;  
    char    s[] = "this is a string";  
    char    c = '\n';  
  
    // Open the file  
    if ( fopen_s( &stream, "fprintf_p.out", "w" ) == 0)  
    {  
        // Format and print data  
        _fprintf_p( stream, "%2$s%1$c", c, s );  
        _fprintf_p( stream, "%d\n", i );  
        _fprintf_p( stream, "%f\n", fp );  
  
        // Close the file  
        fclose( stream );  
    }  
  
    // Verify our data  
    system( "type fprintf_p.out" );  
}  
```  
  
  **esto es una cadena**  
**10**  
**1.500000**   
## Equivalente en .NET Framework  
 [System::IO::StreamWriter::Write](https://msdn.microsoft.com/en-us/library/system.io.streamwriter.write.aspx)  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md)   
 [\_cprintf\_p, \_cprintf\_p\_l, \_cwprintf\_p, \_cwprintf\_p\_l](../../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)   
 [\_cprintf\_s, \_cprintf\_s\_l, \_cwprintf\_s, \_cwprintf\_s\_l](../../c-runtime-library/reference/cprintf-s-cprintf-s-l-cwprintf-s-cwprintf-s-l.md)   
 [printf\_p \(Parámetros de posición\)](../../c-runtime-library/printf-p-positional-parameters.md)   
 [fscanf\_s, \_fscanf\_s\_l, fwscanf\_s, \_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)