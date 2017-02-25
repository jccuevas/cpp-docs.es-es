---
title: "atof, _atof_l, _wtof, _wtof_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wtof_l"
  - "atof"
  - "_atof_l"
  - "_wtof"
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
  - "_tstof"
  - "_ttof"
  - "atof"
  - "stdlib/atof"
  - "math/atof"
  - "_atof_l"
  - "stdlib/_atof_l"
  - "math/_atof_l"
  - "_wtof"
  - "corecrt_wstdlib/_wtof"
  - "_wtof_l"
  - "corecrt_wstdlib/_wtof_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tstof (función)"
  - "atof_l (función)"
  - "_atof_l (función)"
  - "atof (función)"
  - "_tstof (función)"
  - "_ttof (función)"
  - "wtof (función)"
  - "_wtof_l (función)"
  - "ttof (función)"
  - "wtof_l (función)"
  - "_wtof (función)"
  - "conversión de cadenas, a valores de punto flotante"
ms.assetid: eb513241-c9a9-4f5c-b7e7-a49b14abfb75
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 26
---
# atof, _atof_l, _wtof, _wtof_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena a double.  
  
## Sintaxis  
  
```  
double atof(  
   const char *str   
);  
double _atof_l(  
   const char *str,  
   _locale_t locale  
);  
double _wtof(  
   const wchar_t *str   
);  
double _wtof_l(  
   const wchar_t *str,  
   _locale_t locale  
);  
```  
  
#### Parámetros  
 `str`  
 Cadena que se va a convertir.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## Valor devuelto  
 Cada función devuelve el valor de `double` generado interpretar los caracteres de entrada como un número.  El valor devuelto es 0,0 si la entrada no se puede convertir en un valor de ese tipo.  
  
 En todos los casos que se fuera\-de\- intervalo, el errno se establece en `ERANGE`.  Si el parámetro pasado es `NULL`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven 0.  
  
## Comentarios  
 Estas funciones convierten una cadena de caracteres a un de precisión doble, valor de punto flotante.  
  
 La cadena de entrada es una secuencia de caracteres que se pueden interpretar como valor numérico del tipo especificado.  La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número.  Este carácter puede ser el carácter null \(“\\0” o L'\\0\) que termina la cadena.  
  
 El argumento de `str` a `atof` y a `_wtof` tiene el siguiente formato:  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\] \[`.digits`\] \[ {`d` &#124; `D` &#124; `e` &#124; `E` }\[`sign`\]`digits`\]  
  
 `whitespace` consta del espacio o caracteres de tabulación, se omiten que; `sign` está más \(\+\) o menos \(–\); y `digits` es uno o más dígitos decimales.  Si ningún dígitos aparecen antes del separador decimal, al menos uno debe aparecer después del separador decimal.  Los dígitos decimales pueden ir seguidos por un exponente, formada por una letra preliminar \(`d`, `D`, `e`, o `E`\) y un entero decimal opcionalmente firmado.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstof`|`atof`|`atof`|`_wtof`|  
|`_ttof`|`atof`|`atof`|`_wtof`|  
  
## Requisitos  
  
|Rutina\(s\)|Encabezado necesario|  
|-----------------|--------------------------|  
|`atof`|\<math.h y\> stdlib.h \<\>|  
|`_atof_l`|\<math.h y\> stdlib.h \<\>|  
|`_wtof`, `_wtof_l`|\<stdlib.h\> o \<wchar.h\>|  
  
## Ejemplo  
 Este programa muestra cómo los números almacenados como cadenas se pueden convertir en valores numéricos mediante la función de `atof` .  
  
```  
// crt_atof.c  
//  
// This program shows how numbers stored as   
// strings can be converted to numeric  
// values using the atof function.  
  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    double  value = 0;  
  
    // An example of the atof function  
    // using leading and training spaces.  
    str = "  3336402735171707160320 ";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
    // Another example of the atof function  
    // using the 'd' exponential formatting keyword.  
    str = "3.1412764583d210";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
    // An example of the atof function  
    // using the 'e' exponential formatting keyword.  
    str = "  -2309.12E-15";  
    value = atof( str );  
    printf( "Function: atof( \"%s\" ) = %e\n", str, value );  
  
}  
```  
  
  **Función: atof \(“3336402735171707160320 "\) \= 3.336403e\+021**  
**Función: atof \(“3.1412764583d210”\) \= 3.141276e\+210**  
**Función: atof \(“\-2309.12E\-15”\) \= \-2.309120e\-012**   
## Equivalente en .NET Framework  
  
-   [System::Convert::ToSingle](https://msdn.microsoft.com/en-us/library/system.convert.tosingle.aspx)  
  
-   [System::Convert::ToDouble](https://msdn.microsoft.com/en-us/library/system.convert.todouble.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)