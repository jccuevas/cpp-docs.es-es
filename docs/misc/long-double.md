---
title: "Long double | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.types"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "long double de 10 bytes"
  - "Windows de 16 bits"
  - "Windows de 32 bits"
  - "long double de 8 bytes"
  - "precisión de 80 bits"
  - "precisión de 80 bits"
  - "long double de 8 bytes"
  - "long double"
ms.assetid: bb581e20-b5c2-4079-8ee8-ac6739a37852
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Long double
Las versiones de 16 bits anteriores de Microsoft C\/C\+\+ y Microsoft Visual C\+\+ admitidos `long double`, tipo de datos de la precisión de 80 bits.  En Win32 que programa, sin embargo, se asigna a `double`, tipo de datos de 64 bits del tipo de datos de `long double` de precisión.  La biblioteca en tiempo de ejecución de Microsoft proporciona versiones de `long double` de las funciones matemáticas solo por compatibilidad con versiones anteriores.  Los prototipos de función de `long double` son idénticos a los prototipos para sus homólogos de `double` , salvo que el tipo de datos de `long``double` reemplaza el tipo de datos de `double` .  Las versiones de `long double` de estas funciones no deben usarse en código nuevo.  
  
### Double funciona y sus homólogos de doble de Su Long  
  
|Función|Doble largo<br /><br /> equivalente|Función|Doble largo<br /><br /> equivalente|  
|-------------|---------------------------------|-------------|---------------------------------|  
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|`acosl`|[frexp](../c-runtime-library/reference/frexp.md)|`frexpl`|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|`asinl`|[\_hypot](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|`_hypotl`|  
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|`atanl`|[ldexp](../c-runtime-library/reference/ldexp.md)|`ldexpl`|  
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|`atan2l`|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|`logl`|  
|[atof](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|`_atold`|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|`log10l`|  
|[Funciones Bessel s, j1, jn](../misc/bessel-functions-j0-j1-jn.md)|`j0l, j1l, jnl`|[\_matherr](../c-runtime-library/reference/matherr.md)|`_matherrl`|  
|[Funciones Bessel y0, y1, yn](../Topic/Bessel%20Functions:%20_y0,%20_y1,%20_yn.md)|`y0l, y1l, ynl`|[modf](../c-runtime-library/reference/modf-modff-modfl.md)|`modfl`|  
|[\_cabs](../c-runtime-library/reference/cabs.md)|`_cabsl`|[pow](../c-runtime-library/reference/pow-powf-powl.md)|`powl`|  
|[ceil](../c-runtime-library/reference/ceil-ceilf-ceill.md)|`ceill`|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|`sinl`|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|`cosl`|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|`sinhl`|  
|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|`coshl`|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|`sqrtl`|  
|[exp](../c-runtime-library/reference/exp-expf.md)|`expl`|[strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md)|`_strtold`|  
|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|`fabsl`|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|`tanl`|  
|[floor](../c-runtime-library/reference/floor-floorf-floorl.md)|`floorl`|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|`tanhl`|  
|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|`fmodl`|||  
  
## Vea también  
 [Rutinas de tiempo de ejecución por categoría](../c-runtime-library/run-time-routines-by-category.md)