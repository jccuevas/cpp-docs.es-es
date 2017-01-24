---
title: "strtoul, _strtoul_l, wcstoul, _wcstoul_l | Microsoft Docs"
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
  - "_wcstoul_l"
  - "_strtoul_l"
  - "strtoul"
  - "wcstoul"
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
  - "strtoul"
  - "_tcstoul"
  - "wcstoul"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_strtoul_l (función)"
  - "_tcstoul (función)"
  - "_wcstoul_l (función)"
  - "conversión de cadenas, a enteros"
  - "strtoul (función)"
  - "strtoul_l (función)"
  - "tcstoul (función)"
  - "wcstoul (función)"
  - "wcstoul_l (función)"
ms.assetid: 38f2afe8-8178-4e0b-8bbe-d5c6ad66e3ab
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtoul, _strtoul_l, wcstoul, _wcstoul_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte cadenas en un valor entero largo sin signo.  
  
## Sintaxis  
  
```  
unsigned long strtoul(  
   const char *nptr,  
   char **endptr,  
   int base   
);  
unsigned long _strtoul_l(  
   const char *nptr,  
   char **endptr,  
   int base,  
   _locale_t locale  
);  
unsigned long wcstoul(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   int base   
);  
unsigned long _wcstoul_l(  
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
 `strtoul` devuelve el valor convertido, si existe, o `ULONG_MAX` si se produce un desbordamiento.  `strtoul` devuelve 0 si no se puede realizar ninguna conversión.  `wcstoul` devuelve valores de manera parecida a `strtoul`.  Para ambas funciones, `errno` se establece en `ERANGE` si se produce un desbordamiento o subdesbordamiento.  
  
 Vea [\_doserrno, errno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre este y otros códigos de retorno.  
  
## Comentarios  
 Cada una de estas funciones convierte la cadena de entrada `nptr` en un valor `unsigned` `long`.  
  
 `strtoul` deja de leer la cadena `nptr` en el primer carácter que no reconoce como parte de un número.  Puede tratarse del carácter nulo final o del primer carácter numérico mayor o igual que `base`.  El valor de la categoría `LC_NUMERIC` de la configuración regional determina el reconocimiento de caracteres de base en `nptr`. Para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Los objetos `strtoul` y  `wcstoul` usan la configuración regional actual; los objetos `_strtoul_l` y  `_wcstoul_l` son idénticos, salvo que, en cambio, utilizan la configuración regional que se pasa.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que señala `endptr`.  Si no se puede realizar ninguna conversión \(no se encontraron dígitos válidos o se especificó una base no válida\), el valor de `nptr` se almacena en la ubicación a la que señala `endptr`.  
  
 `wcstoul` es una versión con caracteres anchos de `strtoul`; su argumento `nptr` es una cadena de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstoul`|`strtoul`|`strtoul`|`wcstoul`|  
|`_tcstoul_l`|`strtoul_l`|`_strtoul_l`|`_wcstoul_l`|  
  
 `strtoul` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 \[`whitespace`\] \[{`+` &#124; `–`}\] \[`0` \[{ `x` &#124; `X` }\]\] \[`digits`\]  
  
 `whitespace` puede estar formado por caracteres de espacio y tabulación, que se omiten; `digits` es uno o varios dígitos decimales.  El primer carácter que no se ajusta a este formato detiene el análisis.  Si `base` está entre 2 y 36, se usa como base del número.  Si `base` es 0, los caracteres iniciales de la cadena a la que apunta `nptr` se usan para determinar la base.  Si el primer carácter es 0 y el segundo carácter no es 'x' ni 'X', la cadena se interpreta como entero octal.  Si el primer carácter es 0 y el segundo carácter es 'x' o 'X', la cadena se interpreta como entero hexadecimal.  Si el primer carácter está entre 1 y 9, la cadena se interpreta como entero decimal.  A las letras de la 'a' a la 'z' \(o de la 'A' a la 'Z'\) se les asignan los valores del 10 al 35. Solo se admiten las letras cuyos valores asignados son menores que `base`.  El primer carácter que está fuera del intervalo de la base detiene el análisis.  Por ejemplo, si `base` es 0 y el primer carácter examinado es "0", se supone un entero octal y los caracteres "8" o "9 detendrán el análisis.  `strtoul` permite un prefijo de signo más \(`+`\) o menos \(`–`\); un signo menos inicial indica que el valor devuelto es negativo.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strtoul`|\<stdlib.h\>|  
|`wcstoul`|\<stdlib.h\> o \<wchar.h\>|  
|`_strtoul_l`|\<stdlib.h\>|  
|`_wcstoul_l`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
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
 [strtol, wcstol, \_strtol\_l, \_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)