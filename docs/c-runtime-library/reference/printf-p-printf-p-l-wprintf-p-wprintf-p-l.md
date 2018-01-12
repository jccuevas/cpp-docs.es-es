---
title: _printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _printf_p
- _wprintf_p
- _printf_p_l
- _wprintf_p_l
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
- wprintf_p
- _wprintf_p
- printf_p_l
- _printf_p
- printf_p
- _wprintf_p_l
- _printf_p_l
- wprintf_p_l
dev_langs: C++
helpviewer_keywords:
- printf_p function
- printf_p_l function
- wprintf_p function
- wprintf_p_l function
- _tprintf_p_l function
- _wprintf_p function
- _wprintf_p_l function
- _printf_p function
- tprintf_p_l function
- _printf_p_l function
ms.assetid: 1b7e9ef9-a069-45db-af9d-c2730168322e
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 19bbe19ed2cf753d07cfe9c7e42fe533bc90a834
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="printfp-printfpl-wprintfp-wprintfpl"></a>_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l
Imprime el resultado con formato en el flujo de salida estándar y permite especificar el orden en el que se usan los parámetros en la cadena de formato.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _printf_p(  
   const char *format [,  
   argument]...   
);  
int _printf_p_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int _wprintf_p(  
   const wchar_t *format [,  
   argument]...   
);  
int _wprintf_p_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `format`  
 Control de formato.  
  
 `argument`  
 Argumentos opcionales.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve el número de caracteres impreso o un valor negativo si se produce un error.  
  
## <a name="remarks"></a>Comentarios  
 La función `_printf_p` da formato e imprime una serie de caracteres y valores en el flujo de salida estándar, `stdout`. Si los argumentos siguen a la cadena `format`, la cadena `format` debe contener especificaciones que determinen el formato de salida de los argumentos (vea [printf_p [Parámetros de posición]](../../c-runtime-library/printf-p-positional-parameters.md)).  
  
 La diferencia entre `_printf_p` y `printf_s` es que `_printf_p` admite parámetros posicionales, lo que permite especificar el orden en el que se usan los argumentos en la cadena de formato. Para obtener más información, vea [printf_p (Parámetros de posición)](../../c-runtime-library/printf-p-positional-parameters.md).  
  
 `_wprintf_p` es la versión de caracteres anchos de `_printf_p`. Se comportan exactamente igual si el flujo se abre en modo ANSI. `_printf_p` no admite actualmente la salida en un flujo UNICODE.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional del subproceso actual.  
  
> [!IMPORTANT]
>  Asegúrese de que `format` no es una cadena definida por el usuario.  
  
 Si `format` o `argument` es `NULL`, o si la cadena de formato contiene caracteres de formato no válidos, las funciones `_printf_p` y `_wprintf_p` invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve -1 y establece `errno` en `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tprintf_p`|`_printf_p`|`_printf_p`|`_wprintf_p`|  
|`_tprintf_p_l`|`_printf_p_l`|`_printf_p_l`|`_wprintf_p_l`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_printf_p`, `_printf_p_l`|\<stdio.h>|  
|`_wprintf_p`, `_wprintf_p_l`|\<stdio.h> o \<wchar.h>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_printf_p.c  
// This program uses the _printf_p and _wprintf_p  
// functions to choose the order in which parameters  
// are used.  
  
#include <stdio.h>  
  
int main( void )  
{  
   // Positional arguments   
   _printf_p( "Specifying the order: %2$s %3$s %1$s %4$s %5$s.\n",  
              "little", "I'm", "a", "tea", "pot");  
  
   // Resume arguments  
   _wprintf_p( L"Reusing arguments: %1$d %1$d %1$d %1$d\n", 10);  
  
   // Width argument  
   _printf_p("Width specifiers: %1$*2$s", "Hello\n", 10);  
}  
```  
  
```Output  
Specifying the order: I'm a little tea pot.  
Reusing arguments: 10 10 10 10  
Width specifiers:     Hello  
```  
  
## <a name="see-also"></a>Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [E/S de secuencia](../../c-runtime-library/stream-i-o.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [fopen, _wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)   
 [fprintf, _fprintf_l, fwprintf, _fwprintf_l](../../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)   
 [fprintf_s, _fprintf_s_l, fwprintf_s, _fwprintf_s_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf, _scanf_l, wscanf, _wscanf_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf_s, _scanf_s_l, wscanf_s, _wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)   
 [sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)   
 [vprintf (Funciones)](../../c-runtime-library/vprintf-functions.md)