---
title: "_atoi64, _atoi64_l, _wtoi64, _wtoi64_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_atoi64_l"
  - "_wtoi64"
  - "_atoi64"
  - "_wtoi64_l"
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
  - "_atoi64"
  - "_tstoi64"
  - "_ttoi64"
  - "wtoi64"
  - "_tstoi64_l"
  - "atoi64"
  - "_wtoi64_l"
  - "_wtoi64"
  - "wtoi64_l"
  - "_atoi64_l"
  - "atoi64_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tstoi64 (función)"
  - "wtoi64 (función)"
  - "atoi64_l (función)"
  - "_ttoi64 (función)"
  - "conversión de cadenas, a enteros"
  - "wtoi64_l (función)"
  - "atoi64 (función)"
  - "_tstoi64 (función)"
  - "_atoi64_l (función)"
  - "_wtoi64_l (función)"
  - "ttoi64 (función)"
  - "_wtoi64 (función)"
  - "_atoi64 (función)"
ms.assetid: 2c3e30fd-545d-4222-8364-0c5905df9526
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _atoi64, _atoi64_l, _wtoi64, _wtoi64_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en un entero de 64 bits.  
  
## Sintaxis  
  
```  
__int64 _atoi64(  
   const char *str   
);  
__int64 _wtoi64(  
   const wchar_t *str   
);  
__int64 _atoi64_l(  
   const char *str,  
   _locale_t locale  
);  
__int64 _wtoi64_l(  
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
 Cada función devuelve el valor de `__int64` generado interpretar los caracteres de entrada como un número.  El valor devuelto es 0 para `_atoi64` si la entrada no se puede convertir en un valor de ese tipo.  
  
 En el caso de desbordamiento con valores enteros positivos grandes, `_atoi64` devuelve `I64_MAX` y `I64_MIN` en caso de desbordamiento con valores enteros negativos grandes.  
  
 En todos los casos fuera de intervalo, `errno` se establece en `ERANGE`.  Si el parámetro pasado es `NULL`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven 0.  
  
## Comentarios  
 Estas funciones convierten una cadena de caracteres a un valor entero de 64 bits.  
  
 La cadena de entrada es una secuencia de caracteres que se pueden interpretar como valor numérico del tipo especificado.  La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número.  Este carácter podría ser el carácter null \(“\\0” o L'\\0\) que finalizaba la cadena.  
  
 El argumento `str` para `_atoi64` tiene el siguiente formulario:  
  
```  
[whitespace] [sign] [digits]]  
```  
  
 Un `whitespace` consta de caracteres de espacio o tabulación que se omiten, el `sign` puede ser más \(\+\) o menos \(–\) y `digits` son uno o varios dígitos.  
  
 `_wtoi64` es idéntico a `_atoi64`, con la diferencia de que toma una cadena de caracteres anchos como parámetro.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstoi64`|`_atoi64`|`_atoi64`|`_wtoi64`|  
|`_ttoi64`|`_atoi64`|`_atoi64`|`_wtoi64`|  
  
## Requisitos  
  
|Rutinas|Encabezado necesario|  
|-------------|--------------------------|  
|`_atoi64`, `_atoi64_l`|\<stdlib.h\>|  
|`_wtoi64`, `_wtoi64_l`|\<stdlib.h\> o \<wchar.h\>|  
  
## Ejemplo  
 Este programa muestra cómo los números almacenados como cadenas se pueden convertir en valores numéricos mediante las funciones de `_atoi64` .  
  
```  
// crt_atoi64.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the _atoi64 functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    __int64 value = 0;  
  
    // An example of the _atoi64 function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the _atoi64 function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the _atoi64 function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = _atoi64( str );  
    printf( "Function: _atoi64( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **Función: \_atoi64 \(“\-2309 "\) \= \-2309**  
**Función: \_atoi64 \(“314127,64 "\) \= 314127**  
**Función: \_atoi64 \(“3336402735171707160320 "\) \= \-1**  
**Se produjo una condición de desbordamiento.**   
## Equivalente en .NET Framework  
  
-   [System::Convert::ToInt64](https://msdn.microsoft.com/en-us/library/system.convert.toint64.aspx)  
  
-   [System::Convert::ToUInt64](https://msdn.microsoft.com/en-us/library/system.convert.touint64.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)