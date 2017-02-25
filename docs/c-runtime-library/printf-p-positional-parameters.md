---
title: "printf_p (Par&#225;metros de posici&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr120.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
apitype: "DLLExport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_printf_p (función), parámetros posicionales"
  - "printf_p (función), parámetros posicionales"
ms.assetid: beb4fd85-a7aa-4665-9085-2c907a5b9ab0
caps.latest.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 15
---
# printf_p (Par&#225;metros de posici&#243;n)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los parámetros de posición permiten especificar mediante número cuál de los argumentos se debe sustituir en un campo en una cadena de formato.  Las siguientes funciones `printf` de parámetros de posición están disponibles:  
  
 [printf, \_printf\_l, wprintf, \_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)  
 [\_printf\_p, \_printf\_p\_l, \_wprintf\_p, \_wprintf\_p\_l](../c-runtime-library/reference/printf-p-printf-p-l-wprintf-p-wprintf-p-l.md)  
  
 [sprintf, \_sprintf\_l, swprintf, \_swprintf\_l, \_\_swprintf\_l](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)  
 [\_sprintf\_p, \_sprintf\_p\_l, \_swprintf\_p, \_swprintf\_p\_l](../c-runtime-library/reference/sprintf-p-sprintf-p-l-swprintf-p-swprintf-p-l.md)  
  
 [\_cprintf, \_cprintf\_l, \_cwprintf, \_cwprintf\_l](../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)  
 [\_cprintf\_p, \_cprintf\_p\_l, \_cwprintf\_p, \_cwprintf\_p\_l](../c-runtime-library/reference/cprintf-p-cprintf-p-l-cwprintf-p-cwprintf-p-l.md)  
  
 [fprintf, \_fprintf\_l, fwprintf, \_fwprintf\_l](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)  
 [\_fprintf\_p, \_fprintf\_p\_l, \_fwprintf\_p, \_fwprintf\_p\_l](../c-runtime-library/reference/fprintf-p-fprintf-p-l-fwprintf-p-fwprintf-p-l.md)  
  
 [vprintf, \_vprintf\_l, vwprintf, \_vwprintf\_l](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)  
 [\_vprintf\_p, \_vprintf\_p\_l, \_vwprintf\_p, \_vwprintf\_p\_l](../c-runtime-library/reference/vprintf-p-vprintf-p-l-vwprintf-p-vwprintf-p-l.md)  
  
 [vfprintf, \_vfprintf\_l, vfwprintf, \_vfwprintf\_l](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)  
 [\_vfprintf\_p, \_vfprintf\_p\_l, \_vfwprintf\_p, \_vfwprintf\_p\_l](../c-runtime-library/reference/vfprintf-p-vfprintf-p-l-vfwprintf-p-vfwprintf-p-l.md)  
  
 [vsprintf, \_vsprintf\_l, vswprintf, \_vswprintf\_l, \_\_vswprintf\_l](../c-runtime-library/reference/vsprintf-vsprintf-l-vswprintf-vswprintf-l-vswprintf-l.md)  
 [\_vsprintf\_p, \_vsprintf\_p\_l, \_vswprintf\_p, \_vswprintf\_p\_l](../c-runtime-library/reference/vsprintf-p-vsprintf-p-l-vswprintf-p-vswprintf-p-l.md)  
  
## Especificar parámetros de posición  
  
##### Indización de parámetros  
 De forma predeterminada las funciones de posición se comportan exactamente igual que las funciones que no son de posición, si no hay presente formato de posición.  Los parámetros de posición se especifican utilizando el formato “`%m$x`”, donde `m` indica un número ordinal numérico que indica la posición del parámetro en la lista de parámetros, que precede a la cadena de formato y  `x` denota el tipo de carácter del campo de tipo especificado en la función `printf`.  Los parámetros de la lista se indizan empezando por el valor 1 para el primer elemento de la lista y así sucesivamente.  Para obtener más información sobre los caracteres de campo de tipo, consulte [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md).  
  
 Para ver un ejemplo de este comportamiento:  
  
```  
_printf_p("%1$s %2$s", "November", "10");  
```  
  
 se imprimirá  
  
```  
November 10  
```  
  
 No es necesario que el orden de los números utilizados coincida con el orden de los argumentos proporcionados.  Por tanto, el siguiente código es válido:  
  
```  
_printf_p("%2$s %1$s", "November", "10");  
```  
  
 se imprimirá  
  
```  
10 November  
```  
  
 El parámetro se puede utilizar más de una vez al dar formato, a diferencia de las cadenas de formato convencionales, de modo que  
  
```  
_printf_p("%1$d times %1$d is %2$d", 10, 100);  
```  
  
 se imprimirá  
  
```  
10 times 10 is 100  
```  
  
 Sin embargo, todos los argumentos se deben utilizar al menos una vez en algún lugar de la cadena de formato.  
  
 El número máximo de parámetros de posición permitidos en una cadena de formato lo proporciona `_ARGMAX`.  
  
##### Ancho y precisión  
 Cuando se utiliza el símbolo \* para especificar que el ancho o la precisión se debe determinar desde un argumento, la posición del valor de ancho o precisión debe aparecer justo después del símbolo \*.  Por ejemplo,  
  
```  
_printf_p("%1$*2$s","Hello", 10);  
```  
  
 o  
  
```  
_printf_p("%2$*1$s",10, "Hello");  
```  
  
##### Mezclar argumentos de posición y no posición  
 Los parámetros de posición no se pueden mezclar con parámetros no que no sean de posición en la misma cadena de formato.  Sin embargo, las funciones `printf_p` y las funciones relacionadas todavía admiten parámetros que no sean de posición en cadenas de formato que no contengan parámetros de posición.  
  
## Ejemplo  
  
```  
// positional_args.c  
// Positional arguments allow the specification of the order  
// in which arguments are consumed in a formatting string.  
  
#include <stdio.h>  
  
int main(int argc, char *argv[])  
{  
    int     i = 1,  
            j = 2,  
            k = 3;  
    double  x = 0.1,  
            y = 0.2,  
            z = 0.3;  
    char    *s1 = "abc",  
            *s2 = "def",  
            *s3 = "ghi";  
  
    // If positional arguments are unspecified,  
    // normal input order is used.  
    _printf_p("%d %d %d\n", i, j, k);  
  
    // Positional args are numbers indicating the  
    // argument enclosed in curly braces.  
    _printf_p("%3$d %1$d %2$d\n", i, j, k);  
  
    // The same positional argument may be reused.  
    _printf_p("%1$d %2$d %1$d\n", i, j);  
  
    _printf_p("%1$s %2$s %3$s\n", s1, s2, s3);  
  
    _printf_p("%3$s %1$s %2$s\n", s1, s2, s3);  
}  
```  
  
  **1 2 3**  
**3 1 2**  
**1 2 1**  
**abc def ghi**  
**ghi abc def**   
## Vea también  
 [printf \(Caracteres de campo de tipo\)](../c-runtime-library/printf-type-field-characters.md)   
 [printf \(Especificación de ancho\)](../c-runtime-library/printf-width-specification.md)   
 [Especificación de precisión](../c-runtime-library/precision-specification.md)