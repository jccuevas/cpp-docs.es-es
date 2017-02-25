---
title: "_cabs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cabs"
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
  - "cabsl"
  - "_cabs"
  - "_cabsl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cabs (función)"
  - "_cabsl (función)"
  - "valores absolutos"
  - "cabs (función)"
  - "cabsl (función)"
  - "calcular valores absolutos"
ms.assetid: fea292ee-1a39-4a0a-b416-4a189346ff26
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# _cabs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el valor absoluto de un número complejo.  
  
## Sintaxis  
  
```  
double _cabs(   
   struct _complex z   
);  
```  
  
#### Parámetros  
 `z`  
 Número complejo.  
  
## Valor devuelto  
 `_cabs` devuelve el valor absoluto del argumento si correctamente.  En desbordamiento, `_cabs` devuelve `HUGE_VAL` y establece `errno` a `ERANGE`.  Puede cambiar de errores con [\_matherr](../../c-runtime-library/reference/matherr.md).  
  
## Comentarios  
 La función de `_cabs` calcula el valor absoluto de un número complejo, que debe ser una estructura de [\_complex](../../c-runtime-library/standard-types.md)escrito.  La estructura `z` se compone de un componente real `x` y un componente imaginario `y`.  Una llamada a `_cabs` genera un equivalente del valor de la expresión `sqrt`\( `z.x``*``z.x``+``z.y`\*`z.y` \).  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_cabs`|\<math.h\>|  
  
 Para obtener más información de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## Ejemplo  
  
```  
// crt_cabs.c  
/* Using _cabs, this program calculates  
 * the absolute value of a complex number.  
 */  
#include <math.h>  
#include <stdio.h>  
  
int main( void )  
{  
   struct _complex number = { 3.0, 4.0 };  
   double d;  
  
   d = _cabs( number );  
   printf( "The absolute value of %f + %fi is %f\n",  
           number.x, number.y, d );  
}  
```  
  
  **El valor absoluto de 3,000000 \+ 4.000000i es 5,000000**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ABS, laboratorios, llabs, \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [fabs, fabsf, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [labs, llabs](../../misc/labs-llabs.md)