---
title: strtof, _strtof_l, wcstof, _wcstof_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _strtof_l
- wcstof
- strtof
- _wcstof_l
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tcstof
- _tcstof_l
- stdlib/strtof
- strtof
- stdlib/_strtof_l
- _strtof_l
- corecrt_wstdlib/wcstof
- wcstof
- corecrt_wstdlib/_wcstof_l
- _wcstof_l
dev_langs:
- C++
helpviewer_keywords:
- _strtof_l function
- _tcstof function
- _wcstof_l function
- wcstof function
- _tcstof_l function
- strtof function
ms.assetid: 52221b46-876d-4fcc-afb1-97512c17a43b
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 35ee9dd81cb2509e161846870d23b7a995ac5807
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="strtof-strtofl-wcstof-wcstofl"></a>strtof, _strtof_l, wcstof, _wcstof_l
Convierte las cadenas en un valor de punto flotante de precisión sencilla.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
float strtof(  
   const char *nptr,  
   char **endptr   
);  
float _strtof_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
float wcstof(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
float wcstof_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
## <a name="parameters"></a>Parámetros  
 `nptr`  
 Cadena terminada en NULL que se va a convertir.  
  
 `endptr`  
 Puntero al carácter que detiene el examen.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 `strtof` Devuelve el valor del número de punto flotante, excepto cuando la representación produciría desbordamiento, en cuyo caso la función devuelve +/-`HUGE_VALF`. El signo de `HUGE_VALF` coincide con el signo del valor que no se puede representar. `strtof` devuelve 0 si no se puede efectuar ninguna conversión o si se produce un subdesbordamiento.  
  
 `wcstof` devuelve valores de manera parecida a `strtof`. Para ambas funciones, `errno` se establece en `ERANGE` si se produce un desbordamiento o un subdesbordamiento y se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Para obtener más información sobre los códigos de retorno, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 Cada función convierte la cadena de entrada `nptr` en un `float`. La función `strtof` convierte `nptr` en un valor de precisión sencilla. `strtof` deja de leer la cadena `nptr` en el primer carácter que no reconoce como parte de un número. Este puede ser el carácter nulo de terminación. `wcstof` es una versión con caracteres anchos de `strtof`; su argumento `nptr` es una cadena de caracteres anchos. Por lo demás, estas funciones se comportan exactamente igual.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tcstof`|`strtof`|`strtof`|`wcstof`|  
|`_tcstof_l`|`_strtof_l`|`_strtof_l`|`_wcstof_l`|  
  
 El valor de la categoría `LC_NUMERIC` de la configuración regional actual determina el reconocimiento del carácter de base de `nptr`. Para obtener más información, vea [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md). Las funciones que no tienen el sufijo `_l` usan la configuración regional actual; las que tienen el sufijo son idénticas, salvo que usan la configuración regional que se pasa. Para obtener más información, vea [Locale](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que señala `endptr`. Si no se puede efectuar ninguna conversión (no se encontraron dígitos válidos o se especificó una base no válida), el valor de `nptr` se almacena en la ubicación a la que señala `endptr`.  
  
 `strtof` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 [`whitespace`] [`sign`] [`digits`] [`.digits`] [ {`e` &#124; `E`}[`sign`]`digits`]  
  
 Un `whitespace` puede constar de caracteres de espacio y de tabulación, que se omiten; `sign` es más (`+`) o menos (`-`); y `digits` se refiere a uno o varios dígitos decimales. Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base. Los dígitos decimales pueden ir seguidos de un exponente, que consta de una letra inicial (`e` o `E`) y un entero con signo optativo. Si no aparece ni una parte exponencial ni un carácter de base, se supone que un carácter de base sigue al último dígito de la cadena. El primer carácter que no se ajusta a este formato detiene el análisis.  
 
 Las versiones UCRT de estas funciones no admiten la conversión de letras como exponente de estilo Fortran (`d` o `D`). Esta extensión no estándar era compatible con versiones anteriores de CRT y puede que sea un cambio decisivo para el código.
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`strtof`, `_strtof_l`|C: \<stdlib.h> C++: &lt;cstdlib> o \<stdlib.h>|  
|`wcstof`, `_wcstof_l`|C: \<stdlib.h> o \<wchar.h> C++: &lt;cstdlib>, \<stdlib.h> o \<wchar.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
  
```C  
// crt_strtof.c  
// This program uses strtof to convert a  
// string to a single-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   float x;  
  
   string = "3.14159This stopped it";  
   x = strtof(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtof = %f\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
```Output  
string = 3.14159This stopped it  
   strtof = 3.141590  
   Stopped scan at: This stopped it  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod, _strtod_l, wcstod, _wcstod_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol, wcstol, _strtol_l, _wcstol_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul, _strtoul_l, wcstoul, _wcstoul_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, _atof_l, _wtof, _wtof_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [_free_locale](../../c-runtime-library/reference/free-locale.md)