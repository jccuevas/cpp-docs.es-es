---
title: "atol, _atol_l, _wtol, _wtol_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "atol"
  - "_wtol_l"
  - "_wtol"
  - "_atol_l"
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
  - "_atol_l"
  - "_ttol_l"
  - "_tstol_l"
  - "_tstol"
  - "_wtol"
  - "_ttol"
  - "_wtol_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tstol (función)"
  - "atol (función)"
  - "ttol (función)"
  - "_atol_l (función)"
  - "_tstol_l (función)"
  - "conversión de cadenas, a enteros"
  - "_tstol (función)"
  - "_ttol (función)"
  - "_ttol_l (función)"
  - "atol_l (función)"
  - "wtol_l (función)"
  - "_wtol_l (función)"
  - "wtol (función)"
  - "_wtol (función)"
ms.assetid: cedfc21c-2d64-4e9c-bd04-bdf60b12db46
caps.latest.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 22
---
# atol, _atol_l, _wtol, _wtol_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en un entero largo.  
  
## Sintaxis  
  
```  
long atol(  
   const char *str   
);  
long _atol_l(  
   const char *str,  
   _locale_t locale  
);  
long _wtol(  
   const wchar_t *str   
);  
long _wtol_l(  
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
 Cada función devuelve el valor de `long` generado interpretar los caracteres de entrada como un número.  El valor devuelto es 0L para `atol` si la entrada no se puede convertir en un valor de ese tipo.  
  
 En el caso de desbordamiento con valores enteros positivos grandes, `atol` devuelve `LONG_MAX`; en el caso de desbordamiento con valores enteros negativos grandes, se devuelve `LONG_MIN` .  En todos los casos fuera de intervalo, `errno` se establece en `ERANGE`.  Si el parámetro pasado es `NULL`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven 0.  
  
## Comentarios  
 Estas funciones convierten una cadena de caracteres a un valor entero largo \(`atol`\).  
  
 La cadena de entrada es una secuencia de caracteres que se pueden interpretar como valor numérico del tipo especificado.  La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número.  Este carácter puede ser el carácter de `NULL` \(“\\0” o L'\\0\) que termina la cadena.  
  
 El argumento `str` para `atol` tiene el siguiente formulario:  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\]\]  
  
 Un `whitespace` consta de caracteres de espacio o tabulación que se omiten, el `sign` puede ser más \(\+\) o menos \(–\) y `digits` son uno o varios dígitos.  
  
 `_wtol` es idéntico a `atol` salvo que toma una cadena de caracteres anchos.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstol`|`atol`|`atol`|`_wtol`|  
|`_ttol`|`atol`|`atol`|`_wtol`|  
  
## Requisitos  
  
|Rutinas|Encabezado necesario|  
|-------------|--------------------------|  
|`atol`|\<stdlib.h\>|  
|`_atol_l`, `_wtol`, `_wtol_l`|\<stdlib.h y\> wchar.h \<\>|  
  
## Ejemplo  
 Este programa muestra cómo los números almacenados como cadenas se pueden convertir en valores numéricos mediante la función de `atol` .  
  
```  
// crt_atol.c  
// This program shows how numbers stored as  
// strings can be converted to numeric values  
// using the atol functions.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    long    value = 0;  
  
    // An example of the atol function  
    // with leading and trailing white spaces.  
    str = "  -2309 ";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atol function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atol( str );  
    printf( "Function: atol( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **Función: atol \(“\-2309 "\) \= \-2309**  
**Función: atol \(“314127,64 "\) \= 314127**  
**Función: atol \(“3336402735171707160320 "\) \= 2147483647**  
**Se produjo una condición de desbordamiento.**   
## Equivalente en .NET Framework  
  
-   [System::Convert::ToInt32](https://msdn.microsoft.com/en-us/library/system.convert.toint32.aspx)  
  
-   [System::Convert::ToUInt32](https://msdn.microsoft.com/en-us/library/system.convert.touint32.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [\_ecvt](../../c-runtime-library/reference/ecvt.md)   
 [\_fcvt](../../c-runtime-library/reference/fcvt.md)   
 [\_gcvt](../../c-runtime-library/reference/gcvt.md)   
 [setlocale, \_wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [\_atodbl, \_atodbl\_l, \_atoldbl, \_atoldbl\_l, \_atoflt, \_atoflt\_l](../../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)