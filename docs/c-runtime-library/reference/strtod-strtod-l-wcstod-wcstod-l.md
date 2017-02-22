---
title: "strtod, _strtod_l, wcstod, _wcstod_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "wcstod"
  - "_wcstod_l"
  - "_strtod_l"
  - "strtod"
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
  - "_tcstod"
  - "strtod"
  - "wcstod"
  - "_strtod_l"
  - "_wcstod_l"
  - "stdlib/strtod"
  - "corecrt_wstdlib/wcstod"
  - "stdlib/_strtod_l"
  - "corecrt_wstdlib/_wcstod_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_strtod_l (función)"
  - "_tcstod (función)"
  - "_tcstod_l (función)"
  - "_wcstod_l (función)"
  - "conversión de cadenas, a valores de punto flotante"
  - "strtod (función)"
  - "strtod_l (función)"
  - "tcstod (función)"
  - "tcstod_l (función)"
  - "wcstod (función)"
  - "wcstod_l (función)"
ms.assetid: 0444f74a-ba2a-4973-b7f0-1d77ba88c6ed
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# strtod, _strtod_l, wcstod, _wcstod_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convertir las cadenas a un valor de precisión doble.  
  
## Sintaxis  
  
```  
double strtod(  
   const char *nptr,  
   char **endptr   
);  
double _strtod_l(  
   const char *nptr,  
   char **endptr,  
   _locale_t locale  
);  
double wcstod(  
   const wchar_t *nptr,  
   wchar_t **endptr   
);  
double wcstod_l(  
   const wchar_t *nptr,  
   wchar_t **endptr,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `nptr`  
 Cadena terminada en NULL que se va a convertir.  
  
 `endptr`  
 Puntero al carácter que detiene el examen.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 `strtod` devuelve el valor del número de punto flotante, excepto cuando la representación provocaría un desbordamiento, en cuyo caso la función devuelve \+\/\-`HUGE_VAL`.  El signo de `HUGE_VAL` coincide con el signo del valor que no se puede representar.  `strtod` devuelve 0 si no se puede realizar ninguna conversión o si se produce un subdesbordamiento.  
  
 `wcstod` devuelve valores de manera parecida a `strtod`.  Para ambas funciones, `errno` se establece en `ERANGE` si el desbordamiento o subdesbordamiento aparece y se invoca el controlador de parámetro no válido, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  
  
 Vea [\_doserrno, errno, \_sys\_errlist, y \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) para obtener más información sobre estos y otros códigos de retorno.  
  
## Comentarios  
 Cada función convierte la cadena de entrada `nptr` en `double`.  La función de `strtod` convierte `nptr` a un valor de precisión doble.  `strtod` deja de leer la cadena `nptr` en el primer carácter que no reconoce como parte de un número.  Este puede ser el carácter null final.  `wcstod` es una versión con caracteres anchos de `strtod`; su argumento `nptr` es una cadena de caracteres anchos.  Por lo demás, estas funciones se comportan exactamente igual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tcstod`|`strtod`|`strtod`|`wcstod`|  
|`_tcstod_l`|`_strtod_l`|`_strtod_l`|`_wcstod_l`|  
  
 El valor de categoría de `LC_NUMERIC` de la configuración regional actual determina el reconocimiento de carácter de la base de *`nptr`;* para obtener más información, vea [setlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md).  Las funciones sin el sufijo de `_l` utilizan la configuración regional actual; `_strtod_l` es idéntico a `_strtod_l` salvo que utilizan la configuración regional pasado en su lugar.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 Si `endptr` no es `NULL`, se almacena un puntero al carácter que detuvo el análisis en la ubicación a la que señala `endptr`.  Si no se puede realizar ninguna conversión \(no se encontraron dígitos válidos o se especificó una base no válida\), el valor de `nptr` se almacena en la ubicación a la que señala `endptr`.  
  
 `strtod` espera que `nptr` señale a una cadena con el formato siguiente:  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E`}\[`sign`\]`digits`\]  
  
 `whitespace` puede constar de espacio y caracteres de tabulación, que se omiten, `sign` puede ser más \(`+`\) o menos \(`–`\) y `digits` son uno o varios dígitos decimales.  Si no aparece ningún dígito antes del carácter de base, debe aparecer al menos uno después del carácter de base.  Los dígitos decimales pueden ir seguidos por un exponente, que consta de una letra preliminar \(`d`, `D`, `e` o `E`\) y, opcionalmente, un entero con signo.  Si no aparece una parte del exponente ni un carácter de base, se supondrá que el carácter de base sigue el último dígito de la cadena.  El primer carácter que no se ajusta a este formato detiene el análisis.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`strtod`, `_strtod_l`|\<stdlib.h\>|  
|`wcstod`, `_wcstod_l`|\<stdlib.h\> o \<wchar.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_strtod.c  
// This program uses strtod to convert a  
// string to a double-precision value; strtol to  
// convert a string to long integer values; and strtoul  
// to convert a string to unsigned long-integer values.  
//  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   char   *string, *stopstring;  
   double x;  
   long   l;  
   int    base;  
   unsigned long ul;  
  
   string = "3.1415926This stopped it";  
   x = strtod( string, &stopstring );  
   printf( "string = %s\n", string );  
   printf("   strtod = %f\n", x );  
   printf("   Stopped scan at: %s\n\n", stopstring );  
  
   string = "-10110134932This stopped it";  
   l = strtol( string, &stopstring, 10 );  
   printf( "string = %s\n", string );  
   printf("   strtol = %ld\n", l );  
   printf("   Stopped scan at: %s\n\n", stopstring );  
  
   string = "10110134932";  
   printf( "string = %s\n", string );  
  
   // Convert string using base 2, 4, and 8:  
   for( base = 2; base <= 8; base *= 2 )  
   {  
      // Convert the string:  
      ul = strtoul( string, &stopstring, base );  
      printf( "   strtol = %ld (base %d)\n", ul, base );  
      printf( "   Stopped scan at: %s\n", stopstring );  
   }  
}  
```  
  
  **la cadena \= 3.1415926This la detuvieron**  
 **strtod \= 3,141593**  
 **Análisis detenido en: esto lo detuvo**  
**la cadena \= \-10110134932This se detuvieron**  
 **strtol \= \-2147483648**  
 **Análisis detenido en: esto lo detuvo**  
**cadena \= 10110134932**  
 **strtol \= 45 \(base 2\)**  
 **Análisis detenido en: 34932**  
 **strtol \= 4423 \(base 4\)**  
 **Análisis detenido en: 4932**  
 **strtol \= 2134108 \(base 8\)**  
 **Análisis detenido en: 932**   
## Equivalente en .NET Framework  
 [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Interpretación de secuencias de caracteres de varios bytes](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Funciones de conversión de valores de cadena en valores numéricos](../../c-runtime-library/string-to-numeric-value-functions.md)   
 [strtol, wcstol, \_strtol\_l, \_wcstol\_l](../../c-runtime-library/reference/strtol-wcstol-strtol-l-wcstol-l.md)   
 [strtoul, \_strtoul\_l, wcstoul, \_wcstoul\_l](../../c-runtime-library/reference/strtoul-strtoul-l-wcstoul-wcstoul-l.md)   
 [atof, \_atof\_l, \_wtof, \_wtof\_l](../../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)   
 [localeconv](../../c-runtime-library/reference/localeconv.md)   
 [\_create\_locale, \_wcreate\_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [\_free\_locale](../../c-runtime-library/reference/free-locale.md)