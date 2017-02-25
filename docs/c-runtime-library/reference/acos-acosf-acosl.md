---
title: "acos, acosf, acosl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "acosf"
  - "acos"
  - "acosl"
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
  - "api-ms-win-crt-math-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "acos"
  - "acosl"
  - "acosf"
  - "math/acosf"
  - "math/acosl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "acos (función)"
  - "acosf (función)"
  - "acosl (función)"
  - "arco coseno (función)"
  - "funciones trigonométricas"
ms.assetid: 00b89c48-8faf-4824-aa95-fa4349a4975d
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# acos, acosf, acosl
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el arco coseno.  
  
## Sintaxis  
  
```  
double acos(   
   double x   
);  
float acos(  
   float x   
);   // C++ only  
long double acos(  
   long double x  
);   // C++ only  
float acosf(  
   float x   
);  
long double acosl(  
   long double x  
);  
```  
  
#### Parámetros  
 `x`  
 Valor entre – 1 y 1, para el que calcular el arco coseno \(coseno inverso\).  
  
## Valor devuelto  
 La función `acos` devuelve el arco coseno de `x` en el intervalo de 0 a π radianes.  
  
 De forma predeterminada, si `x` es menor que – 1 o mayor que 1, `acos` devuelve un indefinido.  
  
|Entrada|Excepción SEH|Excepción de Matherr|  
|-------------|-------------------|--------------------------|  
|± ∞|`INVALID`|`_DOMAIN`|  
|± QNAN,IND|ninguno|`_DOMAIN`|  
|&#124;x&#124;\>1|`INVALID`|`_DOMAIN`|  
  
## Comentarios  
 Como C\+\+ permite las sobrecargas, puede llamar a las sobrecargas de `acos` que toman y devuelven los tipos `float` y `long double`.  En un programa C, `acos` siempre y devuelve `double`.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|Encabezados opcionales|  
|------------|--------------------------|----------------------------|  
|`acos`, `acosf`, `acosl`|\<math.h\>|\<errno.h\>|  
  
## Ejemplo  
 Este programa solicita un valor del intervalo comprendido entre \-1 y 1.  Los valores de entrada que no estén dentro de este intervalo producen mensajes de error de `_DOMAIN`.  Si se especifica un valor válido, el programa imprime el arco seno y el arco coseno de ese valor.  
  
```  
// crt_asincos.c  
// arguments: 0  
  
#include <math.h>  
#include <stdio.h>  
#include <stdlib.h>  
#include <errno.h>  
  
int main( int ac, char* av[] )  
{  
    double  x,  
            y;  
    errno_t err;   
  
    // argument checking  
    if (ac != 2)  
    {  
        fprintf_s( stderr, "Usage: %s <number between -1 and 1>\n",  
                   av[0]);  
        return 1;  
    }  
  
    // Convert argument into a double value  
    if ((err = sscanf_s( av[1], "%lf", &x )) != 1)  
    {  
        fprintf_s( stderr, "Error converting argument into ",  
                   "double value.\n");  
        return 1;  
    }  
  
    // Arcsine of X  
    y = asin( x );  
    printf_s( "Arcsine of %f = %f\n", x, y );  
  
    // Arccosine of X  
    y = acos( x );  
    printf_s( "Arccosine of %f = %f\n", x, y );  
}  
```  
  
  **Arco seno de 0,000000 \= 0,000000**  
**Arco coseno de 0,000000 \= 1,570796**   
## Equivalente en .NET Framework  
 [System::Math::Acos](https://msdn.microsoft.com/en-us/library/system.math.acos.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [asin, asinf, asinl](../../c-runtime-library/reference/asin-asinf-asinl.md)   
 [atan, atanf, atanl, atan2, atan2f, atan2l](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)   
 [cos, cosf, cosl, cosh, coshf, coshl](../../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)   
 [\_matherr](../../c-runtime-library/reference/matherr.md)   
 [sin, sinf, sinl, sinh, sinhf, sinhl](../../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)   
 [tan, tanf, tanl, tanh, tanhf, tanhl](../../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)