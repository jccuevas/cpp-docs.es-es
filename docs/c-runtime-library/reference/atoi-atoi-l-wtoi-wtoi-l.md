---
title: "atoi, _atoi_l, _wtoi, _wtoi_l | Microsoft Docs"
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
  - "_wtoi"
  - "_wtoi_l"
  - "atoi"
  - "_atoi_l"
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
  - "_tstoi"
  - "_wtoi"
  - "_ttoi"
  - "atoi"
  - "_atoi_l"
  - "_wtoi_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_atoi_l (función)"
  - "ttoi (función)"
  - "atoi_l (función)"
  - "conversión de cadenas, a enteros"
  - "_wtoi (función)"
  - "wtoi_l (función)"
  - "tstoi (función)"
  - "_ttoi (función)"
  - "_tstoi (función)"
  - "_wtoi_l (función)"
  - "atoi (función)"
  - "wtoi (función)"
ms.assetid: ad7fda30-28ab-421f-aaad-ef0b8868663a
caps.latest.revision: 22
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atoi, _atoi_l, _wtoi, _wtoi_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en un entero.  
  
## Sintaxis  
  
```  
int atoi(  
   const char *str   
);  
int _wtoi(  
   const wchar_t *str   
);  
int _atoi_l(  
   const char *str,  
   _locale_t locale  
);  
int _wtoi_l(  
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
 Cada función devuelve el valor de `int` generado interpretar los caracteres de entrada como un número.  El valor devuelto es 0 para `atoi` y `_wtoi`, si la entrada no se puede convertir en un valor de ese tipo.  
  
 En el caso de desbordamiento con valores enteros negativos grandes, se devuelve `LONG_MIN` .  `atoi` y `_wtoi` devuelven `INT_MAX` y `INT_MIN` en estas condiciones.  En todos los casos fuera de intervalo, `errno` se establece en `ERANGE`.  Si el parámetro pasado es `NULL`, se invoca el controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven 0.  
  
## Comentarios  
 Estas funciones convierten una cadena de caracteres a un valor entero \(`atoi` y `_wtoi`\).  La cadena de entrada es una secuencia de caracteres que se pueden interpretar como valor numérico del tipo especificado.  La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número.  Este carácter puede ser el carácter null \(“\\0” o L'\\0\) que termina la cadena.  
  
 El argumento de `str` a `atoi`y a `_wtoi` tiene el siguiente formato:  
  
 \[`whitespace`\] \[`sign`\] \[`digits`\]\]  
  
 Un `whitespace` consta de caracteres de espacio o tabulación que se omiten, el `sign` puede ser más \(\+\) o menos \(–\) y `digits` son uno o varios dígitos.  
  
 Las versiones de estas funciones con el sufijo `_l` son idénticas salvo que usan el parámetro locale pasado en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstoi`|`atoi`|`atoi`|`_wtoi`|  
|`_ttoi`|`atoi`|`atoi`|`_wtoi`|  
  
## Requisitos  
  
|Rutinas|Encabezado necesario|  
|-------------|--------------------------|  
|`atoi`|\<stdlib.h\>|  
|`_atoi_l`, `_wtoi`, `_wtoi_l`|\<stdlib.h\> o \<wchar.h\>|  
  
## Ejemplo  
 Este programa muestra cómo los números almacenados como cadenas se pueden convertir en valores numéricos mediante las funciones de `atoi` .  
  
```  
// crt_atoi.c  
// This program shows how numbers   
// stored as strings can be converted to  
// numeric values using the atoi functions.  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main( void )  
{  
    char    *str = NULL;  
    int     value = 0;  
  
    // An example of the atoi function.  
    str = "  -2309 ";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function.  
    str = "31412764";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
  
    // Another example of the atoi function   
    // with an overflow condition occuring.  
    str = "3336402735171707160320";  
    value = atoi( str );  
    printf( "Function: atoi( \"%s\" ) = %d\n", str, value );  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **Función: atoi \(“\-2309 "\) \= \-2309**  
**Función: atoi \(“31412764 "\) \= 31412764**  
**Función: atoi \(“3336402735171707160320 "\) \= 2147483647**  
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