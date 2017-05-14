---
title: vscanf, vwscanf | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vscanf
- vwscanf
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
- vscanf
- vwscanf
- _vtscanf
dev_langs:
- C++
ms.assetid: d1df595b-11bc-4682-9441-a92616301e3b
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 8f122fc5d04b603fa654d0515287cd0b48f51434
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="vscanf-vwscanf"></a>vscanf, vwscanf
Lee datos con formato del flujo de entrada estándar. Hay disponibles versiones más seguras de estas funciones; vea [vscanf_s, vwscanf_s](../../c-runtime-library/reference/vscanf-s-vwscanf-s.md).  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `format`  
 Cadena de control de formato.  
  
 `arglist`  
 Lista de argumentos de variable.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el número de campos que se han convertido y asignado correctamente; el valor devuelto no incluye los campos leídos pero no asignados. Un valor devuelto de 0 indica que no se ha asignado ningún campo.  
  
 Si `format` es un puntero `NULL`, se invoca al controlador de parámetros no válidos, tal como se explica en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven `EOF` y establecen `errno` en `EINVAL`.  
  
 Para más información sobre estos y otros códigos de error, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 La función `vscanf` lee datos del flujo de entrada estándar `stdin` y los escribe en las ubicaciones que proporciona la lista de argumentos `arglist`. Cada argumento de la lista debe ser un puntero a una variable de un tipo que se corresponda con un especificador de tipo en `format`. Si la copia tiene lugar entre cadenas que se superponen, el comportamiento es indefinido.  
  
> [!IMPORTANT]
>  Cuando use `vscanf` para leer una cadena, especifique siempre un ancho para el formato `%s` (por ejemplo, `"%32s"` en lugar de `"%s"`); de lo contrario, el formato incorrecto de la entrada puede provocar un desbordamiento del búfer. Como alternativa, puede usar [vscanf_s, vwscanf_s](../../c-runtime-library/reference/vscanf-s-vwscanf-s.md) o [fgets](../../c-runtime-library/reference/fgets-fgetws.md).  
  
 `vwscanf` es una versión con caracteres anchos de `vscanf`; el argumento `format` para `vwscanf` es una cadena de caracteres anchos. `vwscanf` y `vscanf` se comportan exactamente igual si el flujo se abre en modo ANSI. `vscanf` no admite la entrada desde un flujo UNICODE.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vtscanf`|`vscanf`|`vscanf`|`vwscanf`|  
  
 Para obtener más información, vea [Campos de especificación de formato: funciones scanf y wscanf](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`vscanf`|\<stdio.h>|  
|`vwscanf`|\<stdio.h> o \<wchar.h>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
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
  
```Output  
  
      71 98.6 h z Byte characters  
36 92.3 y n Wide charactersThe number of fields input is 6  
The contents are: 71 98.599998 h z Byte characters  
The number of fields input is 6  
The contents are: 36 92.300003 y n Wide characters  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [fscanf, _fscanf_l, fwscanf, _fwscanf_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sscanf, _sscanf_l, swscanf, _swscanf_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)   
 [vscanf_s, vwscanf_s](../../c-runtime-library/reference/vscanf-s-vwscanf-s.md)
