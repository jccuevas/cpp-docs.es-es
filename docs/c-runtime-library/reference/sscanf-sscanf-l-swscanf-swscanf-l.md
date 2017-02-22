---
title: "sscanf, _sscanf_l, swscanf, _swscanf_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "swscanf"
  - "sscanf"
  - "_sscanf_l"
  - "_swscanf_l"
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
  - "_sscanf_l"
  - "_stscanf"
  - "swscanf"
  - "_stscanf_l"
  - "sscanf"
  - "_swscanf_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_sscanf_l (función)"
  - "_stscanf (función)"
  - "_stscanf_l (función)"
  - "_swscanf_l (función)"
  - "leer datos, cadenas"
  - "sscanf (función)"
  - "sscanf_l (función)"
  - "cadenas [C++], leer"
  - "cadenas [C++], leer datos de"
  - "stscanf (función)"
  - "stscanf_l (función)"
  - "swscanf (función)"
  - "swscanf_l (función)"
ms.assetid: c2dcf0d2-9798-499f-a4a8-06f7e2b9a80c
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# sscanf, _sscanf_l, swscanf, _swscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Datos con formato lectura de una cadena.  Hay disponibles versiones más seguras de estas funciones; vea [sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md).  
  
## Sintaxis  
  
```  
int sscanf(  
   const char *buffer,  
   const char *format [,  
   argument ] ...   
);  
int _sscanf_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...   
);  
int swscanf(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...   
);  
int _swscanf_l(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   locale_t locale [,  
   argument ] ...   
);  
```  
  
#### Parámetros  
 `buffer`  
 Datos almacenados  
  
 `format`  
 Cadena de control de formato.  Para obtener más información, vea [Especificaciones de formato](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `argument`  
 Argumentos opcionales  
  
 `locale`  
 Configuración regional que se va a usar  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el número de campos convierten y asignados correctamente; el valor devuelto no incluye los campos que se leyeron pero no asignados.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  El valor devuelto es `EOF` en caso de error o si el final de la cadena se alcanza antes de la primera conversión.  
  
 Si `buffer` o `format` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función de `sscanf` lee datos de `buffer` en la ubicación especificada por cada `argument`.  Cada `argument` debe ser un puntero a una variable con un tipo que corresponde a un especificador de tipo en `format`.  El argumento `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento `format` para la función `scanf`.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Al leer una cadena con `sscanf`, especifique siempre un ancho para el formato `%s` \(por ejemplo, `"%32s"` en lugar de `"%s"`\); si no se hace así, el formato incorrecto de la entrada puede provocar una saturación del búfer.  
  
 `swscanf` es una versión con caracteres anchos de `sscanf`; los argumentos a `swscanf` son cadenas de caracteres anchos.  `sscanf`no controla los caracteres hexadecimales multibyte.  `swscanf` no controla caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode.  De lo contrario, los objetos `swscanf` y `sscanf` se comportan de forma idéntica.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_stscanf`|`sscanf`|`sscanf`|`swscanf`|  
|`_stscanf_l`|`_sscanf_l`|`_sscanf_l`|`_swscanf_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`sscanf`, `_sscanf_l`|\<stdio.h\>|  
|`swscanf`, `_swscanf_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_sscanf.c  
// compile with: /W3  
// This program uses sscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string:  
   sscanf( tokenstring, "%80s", s ); // C4996  
   sscanf( tokenstring, "%c", &c );  // C4996  
   sscanf( tokenstring, "%d", &i );  // C4996  
   sscanf( tokenstring, "%f", &fp ); // C4996  
   // Note: sscanf is deprecated; consider using sscanf_s instead  
  
   // Output the data read  
   printf( "String    = %s\n", s );  
   printf( "Character = %c\n", c );  
   printf( "Integer:  = %d\n", i );  
   printf( "Real:     = %f\n", fp );  
}  
```  
  
  **String    \= 15**  
**Character \= 1**  
**Integer:  \= 15**  
**Real:     \= 15,000000**   
## Equivalente en .NET Framework  
 Vea los métodos `Parse`, por ejemplo [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf, \_snprintf, \_snprintf\_l, \_snwprintf, \_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)