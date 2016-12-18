---
title: "_strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l | Microsoft Docs"
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
  - "_strtoi64"
  - "_strtoi64_l"
  - "_wcstoi64_l"
  - "_wcstoi64"
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
  - "api-ms-win-crt-convert-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_strtoi64"
  - "strtoi64"
  - "_stroi64_l"
  - "_wcstoi64_l"
  - "wcstoi64_l"
  - "_wcstoi64"
  - "wcstoi64"
  - "strtoi64_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtoi64 (función)"
  - "_strtoi64_l (función)"
  - "_wcstoi64 (función)"
  - "_wcstoi64_l (función)"
  - "conversión de cadenas, a enteros"
  - "strtoi64 (función)"
  - "strtoi64_l (función)"
  - "wcstoi64 (función)"
  - "wcstoi64_l (función)"
ms.assetid: ea2abc50-7bfe-420e-a46b-703c3153593a
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _strtoi64, _wcstoi64, _strtoi64_l, _wcstoi64_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en un valor `__int64`.  
  
## Sintaxis  
  
```  
__int64 _strtoi64(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
__int64 _wcstoi64(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
__int64 _strtoi64_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
__int64 _wcstoi64_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `nptr`  
 Cadena terminada en NULL que se va a convertir.  
  
 `endptr`  
 Puntero al carácter que detiene el examen.  
  
 `base`  
 Base numérica que se va a usar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `_strtoi64` devuelve el valor que se representa en la cadena `nptr`, excepto cuando la representación produciría desbordamiento, en cuyo caso devuelve `_I64_MAX` o `_I64_MIN`.  La función devuelve 0 si no se puede realizar ninguna conversión.  `_wcstoi64` devuelve valores de manera parecida a `strtoi64`.  
  
 Los objetos `_I64_MAX` y `_I64_MIN` se definen en LIMITS.H.  
  
 Si `nptr` es `NULL` o `base` es distinto de cero y menor que 2 o mayor que 36, `errno` se establece en `EINVAL`.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 La función `_strtoi64`convierte `nptr` en un objeto `__int64`.  Ambas funciones dejan de leer la cadena `nptr` en el primer carácter que no reconocen como parte de un número.  Puede tratarse del carácter nulo final o del primer carácter numérico mayor o igual que `base`.  `_wcstoi64` es una versión con caracteres anchos de `_strtoi64`; su argumento `nptr` es una cadena de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstoi64`|`_strtoi64`|`_strtoi64`|`_wcstoi64`|  
|`_tcstoi64_l`|`_strtoi64_l`|`_strtoi64_l`|`_wcstoi64_l`|  
  
 El valor de la categoría `LC_NUMERIC` de la configuración regional determina el reconocimiento de caracteres de base en `nptr`*.* Para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las funciones sin el sufijo \_l usan la configuración regional actual. `_strtoi64_l`y`_wcstoi64_l`son iguales que las funciones correspondientes sin el sufijo `_l`, salvo que usan la configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que señala `endptr`.  Si no se puede realizar ninguna conversión \(no se encontraron dígitos válidos o se especificó una base no válida\), el valor de `nptr` se almacena en la ubicación a la que señala `endptr`.  
  
 `_strtoi64` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits`\]  
  
 `whitespace` puede estar formado por caracteres de espacio y tabulación, que se omiten; `digits` es uno o varios dígitos decimales.  El primer carácter que no se ajusta a este formato detiene el análisis.  Si `base` está entre 2 y 36, se usa como base del número.  Si `base` es 0, los caracteres iniciales de la cadena a la que apunta `nptr` se usan para determinar la base.  Si el primer carácter es 0 y el segundo carácter no es 'x' ni 'X', la cadena se interpreta como entero octal.  Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal.  Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal.  A las letras de la 'a' a la 'z' \(o de la 'A' a la 'Z'\) se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que `base`.  El primer carácter que está fuera del intervalo de la base detiene el análisis.  Por ejemplo, si `base` es 0 y el primer carácter examinado es "0", se supone un entero octal y los caracteres "8" o "9 detendrán el análisis.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_strtoi64`, `_strtoi64_l`|\<stdlib.h\>|  
|`_wcstoi64`, `_wcstoi64_l`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod, \_strtod\_l, wcstod, \_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)