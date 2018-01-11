---
title: abs, labs, llabs, _abs64 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- abs
- _abs64
- labs
- llabs
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- stdlib/_abs64
- math/abs
- _abs64
- abs
- labs
- math/labs
- llabs
- math/llabs
- cmath/abs
dev_langs: C++
helpviewer_keywords:
- absolute values
- abs function
- abs64 function
- _abs64 function
- calculating absolute values
ms.assetid: 60f789d1-4a1e-49f5-9e4e-0bdb277ea26a
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 64c09dc8c8ce1ce5493ac4b2515c6b0be2910627
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="abs-labs-llabs-abs64"></a>abs, labs, llabs, _abs64
Calcula el valor absoluto del argumento.  
  
## <a name="syntax"></a>Sintaxis  
  
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
  
#### <a name="parameters"></a>Parámetros  
 `n`  
 Valor numérico.  
  
## <a name="return-value"></a>Valor devuelto  
 Las funciones `abs`, `labs`, `llabs` y `_abs64` devuelven el valor absoluto del parámetro `n`. No se devuelve ningún error.  
  
## <a name="remarks"></a>Comentarios  
 Puesto que C++ permite sobrecargas, es posible llamar a las sobrecargas de `abs` que toman y devuelven los valores `long`, `long long`, `float`, `double` y `long double`. Estas sobrecargas se definen en el encabezado \<cmath>. En un programa C, `abs` siempre toma y devuelve un valor int.  
  
 **Específicos de Microsoft**  
  
 Dado que el intervalo de enteros negativos que se puede representar con cualquier tipo de entero es mayor que el intervalo de enteros positivos que se puede representar con ese tipo, se puede proporcionar un argumento a estas funciones que no se pueden convertir. Si el tipo de valor devuelto no puede representar el valor absoluto del argumento, las funciones `abs` devuelven el valor del argumento sin modificar. En concreto, `abs(INT_MIN)` devuelve `INT_MIN`, `labs(LONG_MIN)` devuelve `LONG_MIN`, `llabs(LLONG_MIN)` devuelve `LLONG_MIN` y `_abs64(_I64_MIN)` devuelve `_I64_MIN`. Esto implica que no se pueden usar las funciones `abs` para garantizar un valor positivo.  
  
 **Fin de Específicos de Microsoft**  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado C necesario|Encabezado C++ necesario|  
|-------------|-----------------------|---------------------------|  
|`abs`, `labs`, `llabs`|\<math.h> o \<stdlib.h>|\<cmath>, \<cstdlib>, \<stdlib.h> o \<math.h>|  
|`_abs64`|\<stdlib.h>|\<cstdlib> o \<stdlib.h>|  
  
 Para usar las versiones con sobrecarga de `abs` en C++, debe incluir el encabezado \<cmath>.  
  
## <a name="example"></a>Ejemplo  
 Este programa calcula y muestra los valores absolutos de diversos números.  
  
```C  
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
The absolute value of -4 is 4  
The absolute value of -41567 is 41567  
The absolute value of -9876543210 is 9876543210  
The absolute value of 0xffffffffffffffff is 0x0000000000000001  
Microsoft implementation-specific results:  
 abs(INT_MIN) returns -2147483648  
 labs(LONG_MIN) returns -2147483648  
 llabs(LLONG_MIN) returns -9223372036854775808  
 _abs64(_I64_MIN) returns 0x8000000000000000  
  
```  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs, fabsf, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [imaxabs](../../c-runtime-library/reference/imaxabs.md)