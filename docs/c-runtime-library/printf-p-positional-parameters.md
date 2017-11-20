---
title: "printf_p (Parámetros de posición) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr80.dll
- msvcr100.dll
apitype: DLLExport
dev_langs: C++
helpviewer_keywords:
- _printf_p function, positional parameters
- printf_p function, positional parameters
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 83b3630addfe94c438be21ca2470ade01193a997
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="printfp-positional-parameters"></a>printf_p (Parámetros de posición)
Los parámetros de posición permiten especificar mediante número cuál de los argumentos se debe sustituir en un campo en una cadena de formato. Las siguientes funciones `printf` de parámetros de posición están disponibles:  
  
| Funciones de printf no posicional | Equivalentes de parámetro posicional |  
|---|---|  
|[printf, _printf_l, wprintf, _wprintf_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)|[_printf_p, _printf_p_l, _wprintf_p, _wprintf_p_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)|  
|[sprintf, _sprintf_l, swprintf, _swprintf_l, \__swprintf_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)|[_sprintf_p, _sprintf_p_l, _swprintf_p, _swprintf_p_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)|  
|[_cprintf, _cprintf_l, _cwprintf, _cwprintf_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)|[_cprintf_p, _cprintf_p_l, _cwprintf_p, _cwprintf_p_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)|  
|[fprintf, _fprintf_l, fwprintf, _fwprintf_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)|[_fprintf_p, _fprintf_p_l, _fwprintf_p, _fwprintf_p_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)|  
|[vprintf, _vprintf_l, vwprintf, _vwprintf_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)|[_vprintf_p, _vprintf_p_l, _vwprintf_p, _vwprintf_p_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)|  
|[vfprintf, _vfprintf_l, vfwprintf, _vfwprintf_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)|[_vfprintf_p, _vfprintf_p_l, _vfwprintf_p, _vfwprintf_p_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)|  
|[vsprintf, _vsprintf_l, vswprintf, _vswprintf_l, \__vswprintf_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)|[_vsprintf_p, _vsprintf_p_l, _vswprintf_p, _vswprintf_p_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)|  
  
## <a name="how-to-specify-positional-parameters"></a>Especificación de parámetros de posición  
  
### <a name="parameter-indexing"></a>Indexación de parámetros  
De forma predeterminada las funciones de posición se comportan exactamente igual que las funciones que no son de posición, si no hay presente formato de posición. Los parámetros de posición se especifican utilizando el formato `%n$` al principio del especificador de formato, donde `n` es la posición del parámetro en la lista de parámetros. La posición del parámetro comienza en 1 para el primer argumento después de la cadena de formato. El resto del especificador de formato sigue las mismas reglas que el especificador de formato de `printf`. Para obtener más información acerca de los especificadores de formato, vea [Sintaxis de especificación de formato: funciones printf y wprintf](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md).  
  
Este es un ejemplo del formato de posición:  
  
```C  
_printf_p("%1$s %2$s", "November", "10");  
```  
  
Esto muestra:  
  
```  
November 10  
```  
  
No es necesario que el orden de los números utilizados coincida con el orden de los argumentos. Por ejemplo, esta es una cadena de formato válida:  
  
```C  
_printf_p("%2$s %1$s", "November", "10");  
```  
  
Esto muestra:  
  
```  
10 November  
```  
  
A diferencia de las cadenas de formato tradicional, los parámetros de posición se pueden usar más de una vez en una cadena de formato. Por ejemplo,  
  
```C  
_printf_p("%1$d times %1$d is %2$d", 10, 100);  
```  
  
Esto muestra:  
  
```  
10 times 10 is 100  
```  
  
Todos los argumentos se deben utilizar al menos una vez en algún lugar de la cadena de formato. El número máximo de parámetros de posición permitidos en una cadena de formato lo proporciona `_ARGMAX`.  
  
### <a name="width-and-precision"></a>Ancho y precisión  
Puede usar `*n$` para especificar un parámetro de posición como un especificador de precisión o de ancho, donde `n` es la posición del parámetro de precisión o de ancho en la lista de parámetros. La posición del valor de precisión o de ancho debe aparecer inmediatamente después del símbolo \*. Por ejemplo,  
  
```C  
_printf_p("%1$*2$s","Hello", 10);  
```  
  
o  
  
```C  
_printf_p("%2$*1$s", 10, "Hello");  
```  
  
### <a name="mixing-positional-and-non-positional-arguments"></a>Mezcla de argumentos de posición y no posición  
Los parámetros de posición no se pueden mezclar con parámetros no que no sean de posición en la misma cadena de formato. Si se utiliza cualquier formato de posición, todos los especificadores de formato deben usar el formato de posición. Sin embargo, las funciones `printf_p` y las funciones relacionadas todavía admiten parámetros que no sean de posición en cadenas de formato que no contengan parámetros de posición.  
  
## <a name="example"></a>Ejemplo  
  
```C  
// positional_args.c  
// Build by using: cl /W4 positional_args.c  
// Positional arguments allow the specification of the order  
// in which arguments are consumed in a formatting string.  
  
#include <stdio.h>  
  
int main()  
{  
    int     i = 1,  
            j = 2,  
            k = 3;  
    double  x = 0.1,  
            y = 2.22,  
            z = 333.3333;  
    char    *s1 = "abc",  
            *s2 = "def",  
            *s3 = "ghi";  
  
    // If positional arguments are unspecified,  
    // normal input order is used.  
    _printf_p("%d %d %d\n", i, j, k);  
  
    // Positional arguments are numbers followed by a $ character.  
    _printf_p("%3$d %1$d %2$d\n", i, j, k);  
  
    // The same positional argument may be reused.  
    _printf_p("%1$d %2$d %1$d\n", i, j);  
  
    // The positional arguments may appear in any order.
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);  
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);  
  
    // Precision and width specifiers must be int types.  
    _printf_p("%3$*5$f %2$.*4$f %1$*4$.*5$f\n", x, y, z, j, k);  
}  
```  
  
```Output  
1 2 3
3 1 2
1 2 1
abc def ghi
ghi abc def
333.333300 2.22 0.100
```  
  
## <a name="see-also"></a>Vea también  
 [Sintaxis de especificación de formato: printf y wprintf (funciones)](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md)