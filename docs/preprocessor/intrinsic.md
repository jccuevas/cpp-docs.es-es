---
title: "intrinsic | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "intrinsic_CPP"
  - "vc-pragma.intrinsic"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "intrinsic (pragma)"
  - "pragma (directivas), intrinsic"
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# intrinsic
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica que las llamadas a funciones incluidas en la lista de argumentos de pragma sean intrínsecas.  
  
## Sintaxis  
  
```  
  
#pragma intrinsic( function1 [, function2, ...] )  
```  
  
## Comentarios  
 La directiva pragma **intrinsic** indica al compilador que una función tiene un comportamiento conocido.  El compilador puede llamar a la función y no reemplazar la llamada a función con instrucciones alineadas si ello mejora el rendimiento.  
  
 A continuación se enumeran las funciones de biblioteca con formas intrínsecas.  Una vez detectada una directiva pragma **intrinsic**, se aplica en la primera definición de función que contenga una función intrínseca especificada.  El efecto continúa hasta el final del archivo de código fuente o hasta la aparición de una directiva pragma **function** que especifique la misma función intrínseca.  La directiva pragma **intrinsic** solo se puede usar fuera de una definición de función, en el nivel global.  
  
 Las siguientes funciones tienen formas intrínsecas que se utilizan cuando se especifica [\/Oi](../build/reference/oi-generate-intrinsic-functions.md):  
  
|||||  
|-|-|-|-|  
|[\_disable](../intrinsics/disable.md)|[\_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|  
|[\_enable](../intrinsics/enable.md)|[\_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../misc/labs-llabs.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|  
|[\_inp](../c-runtime-library/inp-inpw-inpd.md)|[\_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|  
|[\_inpw](../c-runtime-library/inp-inpw-inpd.md)|[\_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||  
|[\_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[\_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||  
|[\_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||  
  
 Los programas que usan funciones intrínsecas son más rápidos, porque carecen de la sobrecarga de las llamadas a función, pero pueden tener un mayor tamaño debido al código adicional que se genera.  
  
 **Específico de x86**  
  
 Las formas intrínsecas \_disable y \_enable generan instrucciones en modo kernel para deshabilitar\/habilitar interrupciones, y podrían ser útiles en controladores en modo kernel.  
  
## Ejemplo  
 Compile el código siguiente en la línea de comandos con "cl \-c \-FAs sample.c" y consulte sample.asm para comprobar la conversión a instrucciones x86 CLI y STI:  
  
```  
// pragma_directive_intrinsic.cpp  
// processor: x86  
#include <dos.h>   // definitions for _disable, _enable  
#pragma intrinsic(_disable)  
#pragma intrinsic(_enable)  
void f1(void) {  
   _disable();  
   // do some work here that should not be interrupted  
   _enable();  
}  
int main() {  
}  
```  
  
 **Fin de Específico de x86**  
  
 Las funciones de punto flotante enumeradas a continuación no tienen formas intrínsecas auténticas.  Tienen versiones que pasan argumentos directamente al chip de punto flotante en lugar de insertarlos en la pila del programa:  
  
|||||  
|-|-|-|-|  
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)||  
  
 Las funciones de punto flotante enumeradas a continuación tienen formas intrínsecas auténticas cuando se especifica [\/Oi](../build/reference/oi-generate-intrinsic-functions.md), [\/Og](../build/reference/og-global-optimizations.md) y [\/fp:fast](../build/reference/fp-specify-floating-point-behavior.md) \(o cualquier opción que incluya \/Og: [\/Ox](../build/reference/ox-full-optimization.md), [\/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md) y \/O2\):  
  
|||||  
|-|-|-|-|  
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|  
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl-sinh-sinhf-sinhl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl-tanh-tanhf-tanhl.md)|  
|[cos](../c-runtime-library/reference/cos-cosf-cosl-cosh-coshf-coshl.md)||||  
  
 Puede utilizar [\/fp:strict](../build/reference/fp-specify-floating-point-behavior.md) o [\/Za](../build/reference/za-ze-disable-language-extensions.md) para reemplazar la generación de opciones de punto flotante realmente intrínsecas.  En este caso, las funciones se generan como rutinas de biblioteca que pasan los argumentos directamente al chip de punto flotante, en lugar de insertarlos en la pila del programa.  
  
 Vea [función \#pragma](../preprocessor/function-c-cpp.md) para obtener información y un ejemplo de cómo habilitar\/deshabilitar formas intrínsecas para un bloque de texto de origen.  
  
## Vea también  
 [Directives pragma y la palabra clave \_\_pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)   
 [Intrínsecos del controlador](../intrinsics/compiler-intrinsics.md)