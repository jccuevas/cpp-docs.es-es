---
title: "imaxabs | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "imaxabs"
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
  - "imaxabs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "imaxabs (función)"
ms.assetid: de2566a3-1415-4e9a-91b5-7ac3a49ebf5e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# imaxabs
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Calcula el valor absoluto de un número entero de cualquier tamaño.  
  
## Sintaxis  
  
```  
intmax_t imaxabs(  
   intmax_t n   
);  
```  
  
#### Parámetros  
 *n*  
 Valor entero.  
  
## Valor devuelto  
 La función `imaxabs` devuelve el valor absoluto del argumento.  No se devuelve ningún error.  
  
> [!NOTE]
>  Puesto que el intervalo de enteros negativos que puede representarse mediante `intmax_t` es mayor que el intervalo de enteros positivos que se pueden representar, es posible proporcionar un argumento a `imaxabs` que no se pueda convertir.  Si el tipo devuelto no puede representar el valor absoluto del argumento, el comportamiento de `imaxabs` será indefinido.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`imaxabs`|\<inttypes.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Bibliotecas  
 Todas las versiones de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## Ejemplo  
  
```  
// crt_imaxabs.c  
// Build using: cl /W3 /Tc crt_imaxabs.c  
// This example calls imaxabs to compute an  
// absolute value, then displays the results.  
  
#include <stdio.h>  
#include <stdlib.h>  
#include <inttypes.h>  
  
int main(int argc, char *argv[])  
{  
   intmax_t x = LLONG_MIN + 2;  
  
   printf("The absolute value of %lld is %lld\n", x, imaxabs(x));  
}  
```  
  
  **El valor absoluto de 9223372036854775806 es 9223372036854775806.**   
## Equivalente en .NET Framework  
 [System::Math::Abs](https://msdn.microsoft.com/en-us/library/system.math.abs.aspx)  
  
## Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [ABS, laboratorios, llabs, \_abs64](../../c-runtime-library/reference/abs-labs-llabs-abs64.md)   
 [\_cabs](../../c-runtime-library/reference/cabs.md)   
 [fabs, fabsf, fabsl](../../c-runtime-library/reference/fabs-fabsf-fabsl.md)   
 [labs, llabs](../../misc/labs-llabs.md)