---
title: "_status87, _statusfp, _statusfp2 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_statusfp2"
  - "_statusfp"
  - "_status87"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_statusfp2"
  - "_statusfp"
  - "statusfp2"
  - "_status87"
  - "status87"
  - "statusfp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "funciones de punto flotante, obtener palabra de estado"
  - "números de punto flotante, palabra de estado"
  - "status87 (función)"
  - "palabra de estado, obtener punto flotante"
  - "statusfp (función)"
  - "_statusfp (función)"
  - "_statusfp2 (función)"
  - "statusfp2 (función)"
  - "_status87 (función)"
  - "funciones de punto flotante"
  - "palabra de estado"
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _status87, _statusfp, _statusfp2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Obtiene la palabra de estado de punto flotante.  
  
## Sintaxis  
  
```  
unsigned int _status87( void );  
unsigned int _statusfp( void );  
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)  
```  
  
#### Parámetros  
 `px86`  
 Esta dirección se rellena con la palabra de estado para la unidad de punto flotante x87.  
  
 `pSSE2`  
 Esta dirección se rellena con la palabra de estado para la unidad de punto flotante SSE2.  
  
## Valor devuelto  
 En el caso de `_status87` y `_statusfp`, los bits del valor devuelto indican el estado de punto flotante.  Vea el archivo de inclusión de FLOAT.H para obtener una definición de los bits devueltos por `_statusfp`.  Muchas funciones de la biblioteca matemática modifican la palabra de estado de punto flotante, con resultados imprevisibles.  La optimización puede reordenar, combinar y eliminar operaciones de punto flotante en torno a llamadas a `_status87`, `_statusfp` y funciones relacionadas.  Use la opción de compilador [\/Od \(Deshabilitar \(Depurar\)\)](../../build/reference/od-disable-debug.md) o la directiva pragma de [fenv\_access](../../preprocessor/fenv-access.md) para evitar optimizaciones que reordenan las operaciones de punto flotante.  Los valores devueltos de `_clearfp` y `_statusfp`, así como los parámetros devueltos de `_statusfp2`, son más confiables si se realizan menos operaciones de punto flotante entre estados conocidos de la palabra de estado de punto flotante.  
  
## Comentarios  
 La función `_statusfp` obtiene la palabra de estado de punto flotante.  La palabra de estado es una combinación del estado de procesador de punto flotante y otras condiciones detectadas por el controlador de excepciones de punto flotante, por ejemplo, desbordamiento y subdesbordamiento de la pila de punto flotante.  Las excepciones sin máscara se comprueban antes de que se devuelva el contenido de la palabra de estado.  De esta forma, el llamador recibe información sobre las excepciones pendientes.  En plataformas x86, `_statusfp` devuelve una combinación del estado de punto flotante de x87 y SSE2.  En las plataformas x64, el estado que se devuelve se basa en el estado de MXCSR de SSE.  En las plataformas ARM, `_statusfp` devuelve el estado del registro de FPSCR.  
  
 `_statusfp` es una versión independiente de la plataforma y portable de `_status87`.  Es idéntica a `_status87` en plataformas Intel \(x86\) y también es compatible con las plataformas x64 y ARM.  Para asegurarse de que el código de punto flotante se puede llevar a todas las arquitecturas, use `_statusfp`.  Si solo va a usar plataformas x86, puede usar `_status87` o `_statusfp`.  
  
 Se recomienda `_statusfp2` para los chips \(como Pentium IV\) que tienen procesadores de punto flotante de x87 y de SSE2.  En el caso de `_statusfp2`, las direcciones se rellenan usando la palabra de estado de punto flotante para el procesador de punto flotante de x87 o de SSE2.  En el caso de chips que admite procesadores de punto flotante de x87 y SSE2, EM\_AMBIGUOUS se establece en 1 si se usa `_statusfp` o `_controlfp`, y la acción es ambigua porque podría referirse a la palabra de estado de punto flotante de x87 o SSE2.  La función `_statusfp2` solo se admite en plataformas x86.  
  
 Estas funciones no son útiles para compilaciones [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) o `/clr:pure`, porque Common Language Runtime \(CLR\) solo admite la precisión de punto flotante predeterminada.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_status87`, `_statusfp`, `_statusfp2`|\<float.h\>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## Ejemplo  
  
```  
// crt_statusfp.c  
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c  
// This program creates various floating-point errors and  
// then uses _statusfp to display messages that indicate these problems.  
  
#include <stdio.h>  
#include <float.h>  
#pragma fenv_access(on)  
  
double test( void )  
{  
   double a = 1e-40;  
   float b;  
   double c;  
  
   printf("Status = 0x%.8x - clear\n", _statusfp());  
  
   // Assignment into b is inexact & underflows:   
   b = (float)(a + 1e-40);  
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());  
  
   // c is denormal:   
   c = b / 2.0;   
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",   
            _statusfp());  
  
   // Clear floating point status:   
   _clearfp();  
   return c;  
}  
  
int main(void)  
{  
   return (int)test();  
}  
```  
  
  **Estado \= 0x00000000 \- claro**  
**Estado \= 0x00000003 \- inexacto, subdesbordamiento**  
**Estado \= 0x00080003 \- inexacto, subdesbordamiento, desnormalizado**   
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)   
 [\_clear87, \_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)   
 [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)