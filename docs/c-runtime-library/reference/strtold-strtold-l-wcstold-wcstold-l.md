---
title: "strtold, _strtold_l, wcstold, _wcstold_l | Microsoft Docs"
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
  - "wcstold"
  - "strtold"
  - "_strtold_l"
  - "_wcstold_l"
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
  - "_tcstold_l"
  - "_wcstold_l"
  - "_tcstold"
  - "strtold"
  - "_strtold_l"
  - "wcstold"
dev_langs: 
  - "C++"
ms.assetid: 928c0c9a-bc49-445b-8822-100eb5954115
caps.latest.revision: 8
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# strtold, _strtold_l, wcstold, _wcstold_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte cadenas en un valor de punto flotante de precisión doble largo.  
  
## Sintaxis  
  
```  
long double strtold(  
   const char *nptr,  
   char **endptr   
);  
long double _strtold_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
long double wcstold(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
long double wcstold_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `nptr`  
 Cadena terminada en NULL que se va a convertir.  
  
 `endptr`  
 Puntero al carácter que detiene el análisis.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `strtold` devuelve el valor del número de punto flotante, como un objeto `long double`, excepto cuando la representación provocaría un desbordamiento, en cuyo caso la función devuelve \+\/\- `HUGE_VALL`.  El signo de `HUGE_VALL` coincide con el signo del valor que no se puede representar.  `strtold` devuelve 0 si no se puede realizar ninguna conversión o si se produce un subdesbordamiento.  
  
 `wcstold` devuelve valores de manera parecida a `strtold`.  Para ambas funciones, `errno` se establece en `ERANGE` si el desbordamiento o subdesbordamiento aparece y se invoca el controlador de parámetro no válido, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Para obtener más información sobre los códigos de retorno, vea [errno, \_doserrno, \_sys\_errlist y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## Comentarios  
 Cada función convierte la cadena de entrada `nptr` en `long double`.  La función `strtold` convierte `nptr` en un valor de doble precisión largo.  `strtold` deja de leer la cadena `nptr` en el primer carácter que no reconoce como parte de un número.  Este puede ser el carácter null final.  La versión de caracteres anchos de `strtold` es `wcstold`; su argumento `nptr` es una cadena de caracteres anchos.  De lo contrario, estas tres funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstold`|`strtold`|`strtold`|`wcstold`|  
|`_tcstold_l`|`_strtold_l`|`_strtold_l`|`_wcstold_l`|  
  
 La configuración de la categoría `LC_NUMERIC` de la configuración regional actual determina el reconocimiento de caracteres de base en `nptr`.  Para obtener más información, vea [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las funciones sin el sufijo `_l` usan la configuración regional actual; `_strtold_l` y `_wcstold_l` son idénticas a `_strtold` y `_wcstold` salvo que usan el parámetro locale pasado en lugar de la configuración regional.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, un puntero al carácter que detuvo el análisis se almacena en la ubicación a la que se señala por `endptr`.  Si no se puede realizar ninguna conversión \(no se encontraron dígitos válidos o se especificó una base no válida\), el valor de `nptr` se almacena en la ubicación a la que se señala por `endptr`.  
  
 `strtold` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E`}\[`sign`\]`digits`\]  
  
 `whitespace` puede constar de espacio y caracteres de tabulación, que se omiten, `sign` puede ser más \(`+`\) o menos \(`–`\) y `digits` son uno o varios dígitos decimales.  Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base.  Los dígitos decimales pueden ir seguidos por un exponente, que consta de una letra preliminar \(`d`, `D`, `e` o `E`\) y, opcionalmente, un entero con signo.  Si no aparece una parte del exponente ni un carácter de base, se supondrá que el carácter de base sigue el último dígito de la cadena.  El primer carácter que no se ajusta a este formato detiene el análisis.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strtold`, `_strtold_l`|\<stdlib.h\>|  
|`wcstold`, `_wcstold_l`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_strtold.c  
// Build with: cl /W4 /Tc crt_strtold.c  
// This program uses strtold to convert a  
// string to a long double-precision value.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char *string;  
   char *stopstring;  
   long double x;  
  
   string = "3.1415926535898This stopped it";  
   x = strtold(string, &stopstring);  
   printf("string = %s\n", string);  
   printf("   strtold = %.13Lf\n", x);  
   printf("   Stopped scan at: %s\n\n", stopstring);  
}  
```  
  
  **string \= 3,1415926535898 Esto lo detuvo**  
 **strtold \= 3,1415926535898**  
 **Análisis detenido en: esto lo detuvo**   
## Equivalente en .NET Framework  
 [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtod, \_strtod\_l, wcstod, \_wcstod\_l](../../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)   
 [strtol, wcstol, \_strtol\_l, \_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_create\_locale, \_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)