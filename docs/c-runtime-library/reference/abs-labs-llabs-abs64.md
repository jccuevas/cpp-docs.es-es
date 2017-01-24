---
title: "ABS, laboratorios, llabs, _abs64 | Microsoft Docs"
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
  - "abs"
  - "_abs64"
  - "labs"
  - "llabs"
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
  - "api-ms-win-crt-utility-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "stdlib/_abs64"
  - "math/abs"
  - "_abs64"
  - "abs"
  - "labs"
  - "math/labs"
  - "llabs"
  - "math/llabs"
  - "cmath/abs"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "valores absolutos"
  - "abs (función)"
  - "abs64 (función)"
  - "_abs64 (función)"
  - "calcular valores absolutos"
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
caps.latest.revision: 29
caps.handback.revision: 29
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ABS, laboratorios, llabs, _abs64
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el valor absoluto del argumento.  
  
## Sintaxis  
  
```  
int abs(   
   int n   
);  
long abs(   
   long n   
);   // C++ only  
long long abs(   
   long long n   
);   // C++ only  
double abs(   
   double n   
);   // C++ only  
long double abs(  
   long double n  
);   // C++ only  
float abs(  
   float n   
);   // C++ only  
long labs(  
   long n   
);  
long long llabs(  
   long long n   
);  
__int64 _abs64(   
   __int64 n   
);  
```  
  
#### Parámetros  
 `n`  
 Valor numérico.  
  
## Valor devuelto  
 El `abs`, `labs`, `llabs` y `_abs64` funciones devuelven el valor absoluto del parámetro `n`. No se devuelve ningún error.  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `abs` que toman y devuelven `long`, `long long`, `float`, `double`, y `long double` valores. Estas sobrecargas se definen en el encabezado \< cmath \>. En un programa de C, `abs` siempre toma y devuelve un int.  
  
 **Específicos de Microsoft**  
  
 Dado que el intervalo de enteros negativos que se puede representar mediante el uso de cualquier tipo entero es mayor que el intervalo de números enteros positivos que puede representarse mediante el uso de ese tipo, es posible proporcionar un argumento a estas funciones que no se puede convertir. Si el valor absoluto del argumento no se puede representar el tipo de valor devuelto, el `abs` funciones devuelven el valor del argumento sin cambios. En concreto, `abs(INT_MIN)` devuelve `INT_MIN`, `labs(LONG_MIN)` devuelve `LONG_MIN`, `llabs(LLONG_MIN)` devuelve `LLONG_MIN`, y `_abs64(_I64_MIN)` devuelve `_I64_MIN`. Esto significa que la `abs` no se puede utilizar funciones para garantizar un valor positivo.  
  
 **Fin de Específicos de Microsoft**  
  
## Requisitos  
  
|Rutina|Encabezado necesario de C|Encabezado de C\+\+ necesario|  
|------------|-------------------------------|-----------------------------------|  
|`abs`, `labs`, `llabs`|\< math.h \> o \< stdlib.h \>|\< cmath \>, \< cstdlib \>, \< stdlib.h \> o \< math.h \>|  
|`_abs64`|\<stdlib.h\>|\< cstdlib \> o \< stdlib.h \>|  
  
 Para usar las versiones sobrecargadas de `abs` en C\+\+, debe incluir el encabezado \< cmath \>.  
  
## Ejemplo  
 Este programa calcula y muestra los valores absolutos de varios números.  
  
```c  
// crt_abs.c  
// Build: cl /W3 /TC crt_abs.c  
// This program demonstrates the use of the abs function  
// by computing and displaying the absolute values of  
// several numbers.  
  
#include <stdio.h>  
#include <math.h>  
#include <stdlib.h>  
#include <limits.h>  
  
int main( void )  
{  
    int ix = -4;  
    long lx = -41567L;  
    long long llx = -9876543210LL;  
    __int64 wx = -1;  
  
    // absolute 32 bit integer value  
    printf_s("The absolute value of %d is %d\n", ix, abs(ix));  
  
    // absolute long integer value  
    printf_s("The absolute value of %ld is %ld\n", lx, labs(lx));  
  
    // absolute long long integer value  
    printf_s("The absolute value of %lld is %lld\n", llx, llabs(llx));  
  
    // absolute 64 bit integer value  
    printf_s("The absolute value of 0x%.16I64x is 0x%.16I64x\n", wx,   
        _abs64(wx));  
  
    // Integer error cases:  
    printf_s("Microsoft implementation-specific results:\n");  
    printf_s(" abs(INT_MIN) returns %d\n", abs(INT_MIN));  
    printf_s(" labs(LONG_MIN) returns %ld\n", labs(LONG_MIN));  
    printf_s(" llabs(LLONG_MIN) returns %lld\n", llabs(LLONG_MIN));  
    printf_s(" _abs64(_I64_MIN) returns 0x%.16I64x\n", _abs64(_I64_MIN));  
}  
```  
  
```Output  
El valor absoluto de -4 es el valor absoluto de-41567 es 41567 el valor absoluto de-9876543210 es 9876543210 es el valor absoluto de 0xffffffffffffffff de 4 resultados de específico de la implementación de Microsoft de 0 x 0000000000000001: abs(INT_MIN) devuelve -2147483648 labs(LONG_MIN) devuelve -2147483648 llabs(LLONG_MIN) devuelve -9223372036854775808 _abs64(_I64_MIN) devuelve 0 x 8000000000000000  
  
```  
  
## Equivalente en .NET Framework  
 [System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs, fabsf, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [imaxabs](../../c-runtime-library/reference/imaxabs.md)