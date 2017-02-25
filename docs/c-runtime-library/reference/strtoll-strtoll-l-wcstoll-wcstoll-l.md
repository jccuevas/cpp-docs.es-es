---
title: "strtoll, _strtoll_l, wcstoll, _wcstoll_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "strtoll"
  - "wcstoll"
  - "_strtoll_l"
  - "_wcstoll_l"
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
  - "_strtoll_l"
  - "_tcstoll_l"
  - "_tcstoll"
  - "_wcstoll_l"
  - "strtoll"
  - "wcstoll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtoll_l (función)"
  - "_tcstoll (función)"
  - "_tcstoll_l (función)"
  - "_wcstoll_l (función)"
  - "strtoll (función)"
  - "wcstoll (función)"
ms.assetid: e2d05dcf-d3b2-4291-9e60-dee77e540fd7
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# strtoll, _strtoll_l, wcstoll, _wcstoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en un valor `long long`.  
  
## Sintaxis  
  
```  
long long strtoll(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
long long wcstoll(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
long long _strtoll_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
long long _wcstoll_l(  
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
 Puntero al carácter que detiene el análisis.  
  
 `base`  
 Base numérica que se va a usar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `strtoll` devuelve el valor que se representa en la cadena `nptr`, excepto cuando la representación produciría desbordamiento, en cuyo caso, devuelve `LLONG_MAX` o `LLONG_MIN`.  La función devuelve 0 si no se puede realizar ninguna conversión.  `wcstoll` devuelve valores de manera parecida a `strtoll`.  
  
 Los objetos `LLONG_MAX` y `LLONG_MIN` se definen en LIMITS.H.  
  
 Si `nptr` es `NULL` o `base` es distinto de cero y menor que 2 o mayor que 36, `errno` se establece en `EINVAL`.  
  
 Para obtener más información sobre los códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 La función `strtoll` convierte `nptr` en `long long`.  Ambas funciones dejan de leer la cadena `nptr` en el primer carácter que no reconocen como parte de un número.  Este puede ser el carácter nulo final o bien, o puede ser el primer carácter numérico mayor o igual que `base`.  `wcstoll` es una versión con caracteres anchos de `strtoll`; su argumento `nptr` es una cadena de caracteres anchos.  De lo contrario, estas tres funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstoll`|`strtoll`|`strtoll`|`wcstoll`|  
|`_tcstoll_l`|`_strtoll_l`|`_strtoll_l`|`_wcstoll_l`|  
  
 El valor de la categoría `LC_NUMERIC` de la configuración regional determina el reconocimiento de caracteres de base en `nptr`; para obtener más información, vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las funciones que no tienen el sufijo `_l` usan la configuración regional actual; `_strtoll_l` y `_wcstoll_l` son idénticas a las funciones correspondientes que no tienen el sufijo, salvo que usan en su lugar la configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, un puntero al carácter que detuvo el análisis se almacena en la ubicación a la que se señala por `endptr`.  Si no se puede realizar ninguna conversión \(no se encontraron dígitos válidos o se especificó una base no válida\), el valor de `nptr` se almacena en la ubicación a la que se señala por `endptr`.  
  
 `strtoll` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits` &#124; `letters`\]  
  
 Un `whitespace` puede constar de caracteres de espacio y de tabulación, que se ignoran; `digits` son uno o varios dígitos decimales; `letters` son una o varias letras de la 'a' a la 'z' \(o de la 'A' a la 'Z'\).  El primer carácter que no se ajusta a este formato detiene el análisis.  Si `base` está entre 2 y 36, se usa como base del número.  Si `base` es 0, los caracteres iniciales de la cadena a la que apunta `nptr` se utilizan para determinar la base.  Si el primer carácter es '0' y el segundo carácter no es 'x' o 'X', la cadena se interpreta como entero octal.  Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal.  Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal.  A las letras de la 'a' a la 'z' \(o de la 'A' a la 'Z'\) se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que `base`.  El primer carácter que está fuera del intervalo de la base detiene el análisis.  Por ejemplo, si `base` es 0 y el primer carácter examinado es "0", se supone un entero octal y los caracteres "8" o "9 detendrán el análisis.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strtoll`, `_strtoll_l`|\<stdlib.h\>|  
|`wcstoll`, `_wcstoll_l`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod, \_strtod\_l, wcstod, \_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol, wcstol, \_strtol\_l, \_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)