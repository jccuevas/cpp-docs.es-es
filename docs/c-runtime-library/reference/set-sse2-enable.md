---
title: "_set_SSE2_enable | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_SSE2_enable"
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
  - "_set_SSE2_enable"
  - "set_SSE2_enable"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_SSE2_enable (función)"
  - "instrucciones de Extensiones SIMD de transmisión por secuencias 2"
  - "set_SSE2_enable (función)"
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _set_SSE2_enable
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Habilita o deshabilita el uso de instrucciones de [Extensiones SIMD de streaming 2](http://msdn.microsoft.com/es-es/f98440eb-73a9-4f96-b203-ac41bb6701ea) \(SSE2\) en rutinas matemáticas CRT. \(Esta función no está disponible en las arquitecturas x64 porque SSE2 está habilitada de forma predeterminada.\)  
  
## Sintaxis  
  
```  
int _set_SSE2_enable(  
   int flag  
);  
```  
  
#### Parámetros  
 `flag`  
 1 para habilitar la implementación SSE2; 0 para deshabilitar la implementación SSE2.  De forma predeterminada, la implementación SSE2 está habilitada en los procesadores que lo admiten.  
  
## Valor devuelto  
 Distinto de cero si se habilita la implementación SSE2; cero si se deshabilita la implementación SSE2.  
  
## Comentarios  
 Las siguientes funciones tienen implementaciones SSE2 que se pueden habilitar mediante `_set_SSE2_enable`:  
  
-   [atan](../../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)  
  
-   [ceil](../../c-runtime-library/reference/ceil-ceilf-ceill.md)  
  
-   [exp](../../c-runtime-library/reference/exp-expf.md)  
  
-   [floor](../../c-runtime-library/reference/floor-floorf-floorl.md)  
  
-   [log](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [log10](../../c-runtime-library/reference/log-logf-log10-log10f.md)  
  
-   [modf](../../c-runtime-library/reference/modf-modff-modfl.md)  
  
-   [pow](../../c-runtime-library/reference/pow-powf-powl.md)  
  
 Las implementaciones SSE2 de estas funciones podrían dar respuestas ligeramente distintas que las implementaciones predeterminadas, porque los valores intermedios SSE2 son cantidades de punto flotante de 64 bits pero valores intermedios de implementación predeterminada son 80 cantidades de punto flotante mordidas.  
  
> [!NOTE]
>  Si utiliza la opción del compilador de [\/Oi \(Genere las funciones intrínsecas\)](../../build/reference/oi-generate-intrinsic-functions.md) de compilar el proyecto, puede parecer que `_set_SSE2_enable` no tiene ningún efecto.  La opción del compilador `/Oi` proporciona al compilador autoridad para utilizar intrínseca para reemplazar las llamadas de CRT; este comportamiento reemplaza el efecto de `_set_SSE2_enable`.  Si desea garantizar que `/Oi` no reemplace `_set_SSE2_enable`, utilice `/Oi-` de compilar el proyecto.  Esto también puede ser el recomienda en que utiliza otros modificadores de compilador que impliquen `/Oi`.  
  
 La implementación SSE2 solo se utiliza si se enmascaran todas las excepciones.  Uso [\_control87, \_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md) a enmascarar excepciones.  
  
## Requisitos  
  
|Rutina|Encabezado necesario|  
|------------|--------------------------|  
|`_set_SSE2_enable`|\<math.h\>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## Ejemplo  
  
```  
// crt_set_SSE2_enable.c  
// processor: x86  
#include <math.h>  
#include <stdio.h>  
  
int main()  
{  
   int i = _set_SSE2_enable(1);  
  
   if (i)  
      printf("SSE2 enabled.\n");  
   else  
      printf("SSE2 not enabled; processor does not support SSE2.\n");  
}  
```  
  
 **Resultados**  
  
 `SSE2 enabled.`  
  
## Equivalente en .NET Framework  
 No es aplicable Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Platform Invoke Examples](../Topic/Platform%20Invoke%20Examples.md).  
  
## Vea también  
 [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md)