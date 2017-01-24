---
title: "sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_sscanf_s_l"
  - "sscanf_s"
  - "_swscanf_s_l"
  - "swscanf_s"
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
  - "_stscanf_s"
  - "sscanf_s"
  - "swscanf_s"
  - "_swscanf_s_l"
  - "_stscanf_s_l"
  - "_sscanf_s_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_sscanf_s_l (función)"
  - "_stscanf_s (función)"
  - "_stscanf_s_l (función)"
  - "_swscanf_s_l (función)"
  - "leer datos, cadenas"
  - "sscanf_s (función)"
  - "sscanf_s_l (función)"
  - "cadenas [C++], leer"
  - "cadenas [C++], leer datos de"
  - "stscanf_s (función)"
  - "stscanf_s_l (función)"
  - "swscanf_s (función)"
  - "swscanf_s_l (función)"
ms.assetid: 956e65c8-00a5-43e8-a2f2-0f547ac9e56c
caps.latest.revision: 30
caps.handback.revision: 30
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# sscanf_s, _sscanf_s_l, swscanf_s, _swscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato de una cadena. Estas versiones de [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int sscanf_s(  
   const char *buffer,  
   const char *format [,  
   argument ] ...  
);  
int _sscanf_s_l(  
   const char *buffer,  
   const char *format,  
   locale_t locale [,  
   argument ] ...  
);  
int swscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format [,  
   argument ] ...  
);  
int _swscanf_s_l(  
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
 Cadena de control de formato. Para obtener más información, consulta [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `argument`  
 Argumentos opcionales  
  
 `locale`  
 Configuración regional que se va a usar  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es `EOF` en caso de error o si el final de la cadena se alcanza antes de la primera conversión.  
  
 Si `buffer` o `format` es un `NULL` se invoca el puntero, el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `sscanf_s` lee datos de `buffer` en la ubicación que proporcionada por cada `argument`. Los argumentos que están después de la cadena de formato especifican punteros a variables que tienen un tipo que se corresponde a un especificador de tipo en `format`. A diferencia de la versión menos segura `sscanf`, se requiere un parámetro de tamaño de búfer cuando se utilizan caracteres de campo de tipo `c`, `C`, `s`, `S`, o conjuntos de control de cadena que se incluyen en `[]`. El tamaño de búfer en caracteres se debe proporcionar como un parámetro adicional inmediatamente después de cada parámetro de búfer que lo necesite. Por ejemplo, si está leyendo en una cadena, el tamaño de búfer para esa cadena se pasa como se indica a continuación:  
  
 `wchar_t ws[10];`  
  
 `swscanf_s(in_str, L"%9s", ws, (unsigned)_countof(ws)); // buffer size is 10, width specification is 9`  
  
 El tamaño de búfer incluye el valor nulo final. Se puede usar un campo de especificación del ancho para garantizar que el token se ajustará al búfer. Si no se usa ningún campo de especificación de ancho y la lectura de token es demasiado grande como para ajustarse al búfer, no se escribirá ningún valor en dicho búfer.  
  
 En el caso de los caracteres, un carácter individual puede leerse como se indica a continuación:  
  
 `wchar_t wc;`  
  
 `swscanf_s(in_str, L"%c", &wc, 1);`  
  
 En este ejemplo se lee un solo carácter de la cadena de entrada y se almacena en un búfer de caracteres anchos. Al leer varios caracteres para cadenas que no tienen un valor nulo final, se usan enteros sin signo como especificación del ancho y el tamaño de búfer.  
  
 `char c[4];`  
  
 `sscanf_s(input, "%4c", &c, (unsigned)_countof(c)); // not null terminated`  
  
 Para obtener más información, vea [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) y [scanf \(Caracteres de campo de tipo\)](../../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  El parámetro de tamaño es del tipo `unsigned`, no `size_t`. Al compilar para destinos de 64 bits, utilice una conversión de tipos estática para convertir `_countof` o `sizeof` resultados al tamaño correcto.  
  
 El argumento `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento `format` para la función `scanf_s`. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
 `swscanf_s` es una versión con caracteres anchos de `sscanf_s;` los argumentos para `swscanf_s` son cadenas de caracteres anchos.`sscanf_s` no controla caracteres hexadecimales multibyte.`swscanf_s` no controla caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode. De lo contrario, los objetos `swscanf_s` y `sscanf_s` se comportan de forma idéntica.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro de configuración regional que se pasa en lugar de la configuración regional del subproceso actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_stscanf_s`|`sscanf_s`|`sscanf_s`|`swscanf_s`|  
|`_stscanf_s_l`|`_sscanf_s_l`|`_sscanf_s_l`|`_swscanf_s_l`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`sscanf_s`, `_sscanf_s_l`|\<stdio.h\>|  
|`swscanf_s`, `_swscanf_s_l`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_sscanf_s.c  
// This program uses sscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   char  tokenstring[] = "15 12 14...";  
   char  s[81];  
   char  c;  
   int   i;  
   float fp;  
  
   // Input various data from tokenstring:  
   // max 80 character string plus NULL terminator  
   sscanf_s( tokenstring, "%s", s, (unsigned)_countof(s) );  
   sscanf_s( tokenstring, "%c", &c, (unsigned)sizeof(char) );  
   sscanf_s( tokenstring, "%d", &i );  
   sscanf_s( tokenstring, "%f", &fp );  
  
   // Output the data read  
   printf_s( "String    = %s\n", s );  
   printf_s( "Character = %c\n", c );  
   printf_s( "Integer:  = %d\n", i );  
   printf_s( "Real:     = %f\n", fp );  
}  
```  
  
```Output  
Cadena = 15 caracteres = 1 entero: = 15 Real: = 15.000000  
```  
  
## Equivalente en .NET Framework  
 Consulte `Parse` métodos, como [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx).  
  
## Vea también  
 [E\/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [fscanf, \_fscanf\_l, fwscanf, \_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [snprintf, \_snprintf, \_snprintf\_l, \_snwprintf, \_snwprintf\_l](../../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)