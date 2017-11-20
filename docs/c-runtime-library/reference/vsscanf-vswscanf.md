---
title: vsscanf, vswscanf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vsscanf
- vswscanf
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- _vstscanf
- vsscanf
- vswscanf
dev_langs: C++
helpviewer_keywords:
- vswscanf function
- vsscanf function
ms.assetid: e96180f2-df46-423d-b4eb-0a49ab819bde
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 95446e1442f1df98dff5e1819e97c49c75209fda
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="vsscanf-vswscanf"></a>vsscanf, vswscanf
Lee datos con formato de una cadena. Hay disponibles versiones más seguras de estas funciones; vea [vsscanf_s, vswscanf_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int vsscanf(  
   const char *buffer,  
   const char *format,  
   va_list arglist  
);  
int vswscanf(  
   const wchar_t *buffer,  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `buffer`  
 Datos almacenados  
  
 `format`  
 Cadena de control de formato. Para más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
 `arglist`  
 Lista de argumentos de variable.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas funciones devuelve el número de campos que se convierten y asignan correctamente; el valor devuelto no incluye los campos que se leyeron pero no se asignaron. Un valor devuelto de 0 indica que no se ha asignado ningún campo. El valor devuelto es `EOF` en caso de error o si el final de la cadena se alcanza antes de la primera conversión.  
  
 Si `buffer` o `format` es un puntero `NULL`, se invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven -1 y establecen `errno` en `EINVAL`.  
  
 Para obtener información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `vsscanf` lee datos de `buffer` en las ubicaciones que proporciona cada argumento de la lista de argumentos `arglist`. Cada argumento de la lista debe ser un puntero a una variable que tenga un tipo que se corresponda con un especificador de tipo en `format`. El argumento `format` controla la interpretación de los campos de entrada y tiene el mismo formato y función que el argumento `format` para la función `scanf`. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Cuando use `vsscanf` para leer una cadena, especifique siempre un ancho para el formato `%s` (por ejemplo, `"%32s"` en lugar de `"%s"`); de lo contrario, el formato incorrecto de la entrada puede provocar un desbordamiento del búfer.  
  
 `vswscanf` es una versión con caracteres anchos de `vsscanf`; los argumentos a `vswscanf` son cadenas de caracteres anchos. `vsscanf` no controla caracteres hexadecimales multibyte. `vswscanf` no controla caracteres de "zona de compatibilidad" o hexadecimal de ancho completo de Unicode. De lo contrario, los objetos `vswscanf` y `vsscanf` se comportan de forma idéntica.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vstscanf`|`vsscanf`|`vsscanf`|`vswscanf`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`vsscanf`|\<stdio.h>|  
|`vswscanf`|\<stdio.h> o \<wchar.h>|  
  
 Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_vsscanf.c  
// compile with: /W3  
// This program uses vsscanf to read data items  
// from a string named tokenstring, then displays them.  
  
#include <stdio.h>  
#include <stdarg.h>  
  
int call_vsscanf(char *tokenstring, char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vsscanf(tokenstring, format, arglist);  
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
    call_vsscanf(tokenstring, "%80s", s);  
    call_vsscanf(tokenstring, "%c", &c);  
    call_vsscanf(tokenstring, "%d", &i);  
    call_vsscanf(tokenstring, "%f", &fp);  
  
    // Output the data read  
    printf("String    = %s\n", s);  
    printf("Character = %c\n", c);  
    printf("Integer:  = %d\n", i);  
    printf("Real:     = %f\n", fp);  
}  
```  
  
```Output  
String    = 15  
Character = 1  
Integer:  = 15  
Real:     = 15.000000  
```  
  
## <a name="see-also"></a>Vea también  
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [sscanf, _sscanf_l, swscanf, _swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [vsscanf_s, vswscanf_s](../../c-runtime-library/reference/vsscanf-s-vswscanf-s.md)