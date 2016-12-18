---
title: "atoll, _atoll_l, _wtoll, _wtoll_l | Microsoft Docs"
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
  - "_wtoll"
  - "_atoll_l"
  - "_wtoll_l"
  - "atoll"
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
  - "_tstoll_l"
  - "_wtoll"
  - "_atoll_l"
  - "_ttoll"
  - "_tstoll"
  - "_wtoll_l"
  - "atoll"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_atoll_l (función)"
  - "_wtoll (función)"
  - "_wtoll_l (función)"
  - "atoll (función)"
ms.assetid: 5e85fcac-b351-4882-bff2-6e7c469b7fa8
caps.latest.revision: 7
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# atoll, _atoll_l, _wtoll, _wtoll_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Convierte una cadena en un entero `long long`.  
  
## Sintaxis  
  
```  
long long atoll(  
   const char *str   
);  
long long _wtoll(  
   const wchar_t *str   
);  
long long _atoll_l(  
   const char *str,  
   _locale_t locale  
);  
long long _wtoll_l(  
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
 Cada función devuelve el valor `long long` que se produce al interpretar los caracteres de entrada como un número.  El valor devuelto para `atoll` es 0 si la entrada no se puede convertir en un valor de ese tipo.  
  
 Para el desbordamiento con valores enteros positivos grandes, `atoll` devuelve `LLONG_MAX` y para el desbordamiento con valores enteros negativos grandes, devuelve `LLONG_MIN`.  
  
 En todos los casos fuera de intervalo, `errno` se establece en `ERANGE`.  Si el parámetro que se pasa es `NULL`, se invocará el controlador de parámetro no válido, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, estas funciones establecen `errno` en `EINVAL` y devuelven 0.  
  
## Comentarios  
 Estas funciones convierten una cadena de caracteres a un valor entero `long long`.  
  
 La cadena de entrada es una secuencia de caracteres que se pueden interpretar como valor numérico del tipo especificado.  La función deja de leer la cadena de entrada en el primer carácter que no reconoce como parte de un número.  Este carácter podría ser el carácter null \(“\\ 0 " o L' \\ 0 '\) que finaliza la cadena.  
  
 El argumento `str` para `atoll` tiene el siguiente formulario:  
  
```  
[whitespace] [sign] [digits]  
```  
  
 Un `whitespace` consta de caracteres de espacio o tabulación que se omiten, el `sign` puede ser más \(\+\) o menos \(–\) y `digits` son uno o varios dígitos.  
  
 `_wtoll` es idéntico a `atoll`, con la diferencia de que toma una cadena de caracteres anchos como parámetro.  
  
 Las versiones de estas funciones que tienen el sufijo `_l` son idénticas a las versiones que no la tienen, salvo que ellas utilizan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual.  Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
### Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|\_UNICODE y \_MBCS no definidos|\_MBCS definido|\_UNICODE definido|  
|--------------------|-------------------------------------|---------------------|------------------------|  
|`_tstoll`|`atoll`|`atoll`|`_wtoll`|  
|`_tstoll_l`|`_atoll_l`|`_atoll_l`|`_wtoll_l`|  
|`_ttoll`|`_atoll`|`_atoll`|`_wtoll`|  
  
## Requisitos  
  
|Rutinas|Encabezado necesario|  
|-------------|--------------------------|  
|`atoll`, `_atoll_l`|\<stdlib.h\>|  
|`_wtoll`, `_wtoll_l`|\<stdlib.h\> o \<wchar.h\>|  
  
## Ejemplo  
 Este programa muestra cómo utilizar las funciones `atoll` para convertir números almacenados como cadenas en valores numéricos.  
  
```  
// crt_atoll.c  
// Build with: cl /W4 /Tc crt_atoll.c  
// This program shows how to use the atoll   
// functions to convert numbers stored as   
// strings to numeric values.  
#include <stdlib.h>  
#include <stdio.h>  
#include <errno.h>  
  
int main(void)  
{  
    char *str = NULL;  
    long long value = 0;  
  
    // An example of the atoll function  
    // with leading and trailing white spaces.  
    str = "  -27182818284 ";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
  
    // Another example of the atoll function   
    // with an arbitrary decimal point.  
    str = "314127.64";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
  
    // Another example of the atoll function  
    // with an overflow condition occurring.  
    str = "3336402735171707160320";  
    value = atoll(str);  
    printf("Function: atoll(\"%s\") = %lld\n", str, value);  
    if (errno == ERANGE)  
    {  
       printf("Overflow condition occurred.\n");  
    }  
}  
```  
  
  **Función: atoll\("  \-27182818284 "\) \= \-27182818284**  
**Función: atoll\("314127.64"\) \= 314127**  
**Función: atoll\("3336402735171707160320"\) \= 9223372036854775807**  
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