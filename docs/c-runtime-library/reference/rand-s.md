---
title: "rand_s | Microsoft Docs"
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
  - "rand_s"
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
  - "rand_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "números aleatorios criptográficamente seguros"
  - "generación de números pseudoaleatorios"
  - "números, generación de pseudoaleatorios"
  - "números, pseudoaleatorios"
  - "números pseudoaleatorios"
  - "rand_s (función)"
  - "números aleatorios, criptográficamente seguros"
  - "números aleatorios, generar"
ms.assetid: d6a0be60-997d-4904-8411-8aea6839cc94
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# rand_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Genera un número pseudoaleatorio.  Una versión de [rand](../../c-runtime-library/reference/rand.md) con mejoras de seguridad como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## Sintaxis  
  
```  
errno_t rand_s(   unsigned int* randomValue);  
```  
  
## Valor devuelto  
 Cero si es correcto, si no, un código de error.  Si el puntero `randomValue` de entrada es un puntero NULL, la función invoca un controlador no válido de parámetro, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md).  Si la ejecución puede continuar, la función devuelve `EINVAL` y establece en `errno` en `EINVAL`.  Si se produce un error en la función por cualquier otro motivo, \*`randomValue` se establece en 0.  
  
## Comentarios  
 La función de `rand_s` escribe un entero pseudoaleatorio en el intervalo de 0 a `UINT_MAX` al puntero de la entrada.  La función de `rand_s` utiliza el sistema operativo para generar criptográficamente garantiza números aleatorios.  No utiliza el valor generado por la función de [srand](../../c-runtime-library/reference/srand.md) , ni afecta a la secuencia de números aleatorios utilizada por `rand`.  
  
 La función de `rand_s` requiere que `_CRT_RAND_S` constante está definido antes de la instrucción include para que la función está declarada, como en el ejemplo siguiente:  
  
```  
#define _CRT_RAND_S  
#include <stdlib.h>  
```  
  
 `rand_s` depende de [RtlGenRandom](http://msdn.microsoft.com/library/windows/desktop/aa387694) API, que sólo en Windows XP y posterior disponibles.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`rand_s`|\<stdlib.h\>|  
  
 Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_rand_s.c  
// This program illustrates how to generate random  
// integer or floating point numbers in a specified range.  
  
// Remembering to define _CRT_RAND_S prior  
// to inclusion statement.  
#define _CRT_RAND_S  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <limits.h>  
  
int main( void )  
{  
    int             i;  
    unsigned int    number;  
    double          max = 100.0;  
    errno_t         err;  
  
    // Display 10 random integers in the range [ 1,10 ].  
    for( i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %u\n", (unsigned int) ((double)number /  
                       ((double) UINT_MAX + 1 ) * 10.0) + 1);  
    }  
  
    printf_s("\n");  
  
    // Display 10 random doubles in [0, max).  
    for (i = 0; i < 10;i++ )  
    {  
        err = rand_s( &number );  
        if (err != 0)  
        {  
            printf_s("The rand_s function failed!\n");  
        }  
        printf_s( "  %g\n", (double) number /   
                          ((double) UINT_MAX + 1) * max );  
    }  
}  
```  
  
## Resultados del ejemplo  
  
```  
10  
4  
5  
2  
8  
2  
5  
6  
1  
1  
  
32.6617  
29.4471  
11.5413  
6.41924  
20.711  
60.2878  
61.0094  
20.1222  
80.9192  
65.0712  
```  
  
## Equivalente en .NET Framework  
 [System::Random Class](https://msdn.microsoft.com/en-us/library/system.random.aspx)  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [srand](../../c-runtime-library/reference/srand.md)