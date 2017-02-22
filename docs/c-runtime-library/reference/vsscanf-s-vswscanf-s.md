---
title: "vsscanf_s, vswscanf_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vswscanf_s"
  - "vsscanf_s"
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
  - "vsscanf_s"
  - "vswscanf_s"
  - "_vstscanf_s"
dev_langs: 
  - "C++"
ms.assetid: 7b732e68-c6f4-4579-8917-122f5a7876e1
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# vsscanf_s, vswscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Lee datos con formato de una cadena.  Estas versiones de [vsscanf, vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md) tienen mejoras de seguridad, como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
int vsscanf_s(  
   const char *buffer,  
   const char *format,  
   va_list argptr  
);   
int vswscanf_s(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   va_list arglist  
);   
```  
  
#### Parámetros  
 `buffer`  
 Datos almacenados  
  
 `format`  
 Cadena de control de formato.  Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `arglist`  
 Lista de argumentos de variable.  
  
## Valor devuelto  
 Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron.  Un valor devuelto de 0 indica que no se ha asignado ningún campo.  El valor devuelto es `EOF` en caso de error o si el final de la cadena se alcanza antes de la primera conversión.  
  
 Si `buffer` o `format` es un puntero `NULL`, se invoca el controlador de parámetros no válidos, se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones devuelven \-1 y establecen `errno` en `EINVAL`.  
  
 Para obtener más información sobre estos y otros códigos de error, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `vsscanf_s` lee datos del `buffer` en ubicaciones que se proporcionan por cada argumento en la lista de argumentos `arglist`.  Los argumentos de la lista de argumentos especifican punteros a variables que tienen un tipo que se corresponde a un especificador de tipo en `format`.  A diferencia de la versión menos segura `vsscanf`, se requiere un parámetro de tamaño de búfer cuando se utilizan caracteres de campo de tipo `c`, `C`, `s`, `S`, o conjuntos de control de cadena que se incluyen en `[]`.  El tamaño de búfer en caracteres se debe proporcionar como un parámetro adicional inmediatamente después de cada parámetro de búfer que lo necesite.  
  
 El tamaño de búfer incluye el valor nulo final.  Se puede usar un campo de especificación del ancho para garantizar que el token se ajustará al búfer.  Si no se usa ningún campo de especificación de ancho y la lectura de token es demasiado grande como para ajustarse al búfer, no se escribirá ningún valor en dicho búfer.  
  
 Para obtener más información, vea [scanf\_s, \_scanf\_s\_l, wscanf\_s, \_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) y [scanf \(Caracteres de campo de tipo\)](../../c-runtime-library/scanf-type-field-characters.md).  
  
> [!NOTE]
>  El parámetro de tamaño es del tipo `unsigned`, no `size_t`.  
  
 El argumento `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento `format` para la función `scanf_s`.  Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
 `vswscanf_s` es una versión con caracteres anchos de `vsscanf_s`; los argumentos a `vswscanf_s` son cadenas de caracteres anchos.  `vsscanf_s` no controla caracteres hexadecimales multibyte.  `vswscanf_s` no controla caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode.  De lo contrario, los objetos `vswscanf_s` y `vsscanf_s` se comportan de forma idéntica.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_vstscanf_s`|`vsscanf_s`|`vsscanf_s`|`vswscanf_s`|  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`vsscanf_s`|\<stdio.h\>|  
|`vswscanf_s`|\<stdio.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_vsscanf_s.c  
// compile with: /W3  
// This program uses vsscanf_s to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vsscanf_s(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf_s(tokenstring, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    char  tokenstring[] = "15 12 14...";  
    char  s[81];  
    char  c;  
    int   i;  
    float fp;  
  
    // Input various data from tokenstring:  
    // max 80 character string:  
    call_vsscanf_s(tokenstring, "%80s", s, _countof(s));  
    call_vsscanf_s(tokenstring, "%c", &c, sizeof(char));  
    call_vsscanf_s(tokenstring, "%d", &i);  
    call_vsscanf_s(tokenstring, "%f", &fp);  
  
    // Output the data read  
    printf("String    = %s\n", s);  
    printf("Character = %c\n", c);  
    printf("Integer:  = %d\n", i);  
    printf("Real:     = %f\n", fp);  
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
 [scanf, \_scanf\_l, wscanf, \_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, \_sscanf\_l, swscanf, \_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sscanf\_s, \_sscanf\_s\_l, swscanf\_s, \_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf, vswscanf](../../c-runtime-library/reference/vsscanf-vswscanf.md)