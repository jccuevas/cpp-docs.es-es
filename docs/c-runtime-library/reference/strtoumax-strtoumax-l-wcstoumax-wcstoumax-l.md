---
title: "strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l | Microsoft Docs"
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
  - "_wcstoumax_l"
  - "_strtoumax_l"
  - "wcstoumax"
  - "strtoumax"
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
  - "wcstoumax"
  - "_tcstoumax"
  - "_strtoumax_l"
  - "_wcstoumax_l"
  - "_tcstoumax_l"
  - "strtoumax"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtoumax_l (función)"
  - "_wcstoumax_l (función)"
  - "funciones de conversión"
  - "strtoumax (función)"
  - "wcstoumax (función)"
ms.assetid: 566769f9-495b-4508-b9c6-02217a578897
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtoumax, _strtoumax_l, wcstoumax, _wcstoumax_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte cadenas a un valor entero de tipo entero sin signo con mayor valor admitido.  
  
## Sintaxis  
  
```  
uintmax_t strtoumax(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
uintmax_t _strtoumax_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
uintmax_t wcstoumax(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
uintmax_t _wcstoumax_l(  
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
 `strtoumax` devuelve el valor convertido, si existe, o `UINTMAX_MAX` si se produce un desbordamiento.  `strtoumax` devuelve 0 si no se puede realizar ninguna conversión.  `wcstoumax` devuelve valores de manera parecida a `strtoumax`.  Para ambas funciones, `errno` se establece en `ERANGE` si se produce un desbordamiento o subdesbordamiento.  
  
 Para obtener más información sobre los códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada una de estas funciones convierte la cadena de entrada `nptr` en un valor entero `uintmax_t`.  
  
 `strtoumax` deja de leer la cadena `nptr` en el primer carácter que no reconoce como parte de un número.  Este puede ser el carácter nulo final o bien, o puede ser el primer carácter numérico mayor o igual que `base`.  La configuración de la categoría `LC_NUMERIC` de la configuración regional determina el reconocimiento de caracteres de base en `nptr`.  Para obtener más información, vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Los objetos `strtoumax` y `wcstoumax` utilizan la configuración regional actual; los objetos `_strtoumax_l` y `_wcstoumax_l` son idénticos, salvo que, en cambio, utilizan la configuración regional en la que se pasan.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, un puntero al carácter que detuvo el análisis se almacena en la ubicación a la que se señala por `endptr`.  Si no se puede realizar ninguna conversión \(no se encontraron dígitos válidos o se especificó una base no válida\), el valor de `nptr` se almacena en la ubicación a la que se señala por `endptr`.  
  
 La versión de caracteres anchos de `strtoumax` es `wcstoumax`; su argumento `nptr` es una cadena de caracteres anchos.  De lo contrario, estas tres funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstoumax`|`strtoumax`|`strtoumax`|`wcstoumax`|  
|`_tcstoumax_l`|`strtoumax_l`|`_strtoumax_l`|`_wcstoumax_l`|  
  
 `strtoumax` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits` &#124; \[`letters`\]\]  
  
 Un `whitespace` puede constar de caracteres de espacio y de tabulación, que se ignoran; `digits` son uno o varios dígitos decimales; `letters` son una o varias letras de la 'a' a la 'z' \(o de la 'A' a la 'Z'\).  El primer carácter que no se ajusta a este formato detiene el análisis.  Si `base` está entre 2 y 36, se usa como base del número.  Si `base` es 0, los caracteres iniciales de la cadena a la que apunta `nptr` se utilizan para determinar la base.  Si el primer carácter es '0' y el segundo carácter no es 'x' o 'X', la cadena se interpreta como entero octal.  Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal.  Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal.  A las letras de la 'a' a la 'z' \(o de la 'A' a la 'Z'\) se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que `base`.  El primer carácter que está fuera del intervalo de la base detiene el análisis.  Por ejemplo, si `base` es 0 y el primer carácter examinado es "0", se supone un entero octal y los caracteres "8" o "9 detendrían el análisis.  `strtoumax` permite un signo más \(`+`\) o prefijo de signo menos \(`–`\); un signo menos inicial indica que el valor devuelto es el complementos de los dos del valor absoluto de la cadena convertida.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strtoumax`|\<stdlib.h\>|  
|`wcstoumax`|\<stdlib.h\> o \<wchar.h\>|  
|`_strtoumax_l`|\<stdlib.h\>|  
|`_wcstoumax_l`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
 Vea el ejemplo de [strtod](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md).  
  
## Equivalente en .NET Framework  
 [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod, \_strtod\_l, wcstod, \_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtoimax, \_strtoimax\_l, wcstoimax, \_wcstoimax\_l](../../c-runtime-library/reference/strtoimax-strtoimax-l-wcstoimax-wcstoimax-l.md)   
 [strtol, wcstol, \_strtol\_l, \_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [strtoll, \_strtoll\_l, wcstoll, \_wcstoll\_l](../../c-runtime-library/reference/strtoll-strtoll-l-wcstoll-wcstoll-l.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)