---
title: "/arch (x86) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
caps.latest.revision: 33
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 33
---
# /arch (x86)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica la arquitectura para la generación de código en x86.  Consulte también [\/arch \(x64\)](../../build/reference/arch-x64.md) y [\/arch \(ARM\)](../../build/reference/arch-arm.md).  
  
## Sintaxis  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## Argumentos  
 **\/arch:IA32**  
 No especifica ninguna instrucción mejorada y también especifica x87 para los cálculos de punto flotante.  
  
 **\/arch:SSE**  
 Habilita el uso de instrucciones SSE.  
  
 **\/arch:SSE2**  
 Habilita el uso de instrucciones SSE2.  Esta es la instrucción predeterminada en las plataformas x86 si no se especifica ninguna opción de **\/arch**.  
  
 **\/arch:AVX**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.  
  
 **\/arch:AVX2**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 \(AVX2\) de Intel.  
  
## Comentarios  
 Las instrucciones SSE2 y SSE existen en varios procesadores de AMD e Intel.  Las instrucciones AVX existen en los procesadores Intel Sandy Bridge y AMD Bulldozer.  Los procesadores Haswell y Broadwell de Intel y los procesadores basados en Excavator de AMD admiten las instrucciones AVX2.  
  
 Las macros `_M_IX86_FP`, `__AVX__` y `__AVX2__` indican qué opción del compilador **\/arch** se utilizó, si se usó alguna.  Para obtener más información, consulte [Macros predefinidas](../../preprocessor/predefined-macros.md).  La opción **\/arch:AVX2** y la macro `__AVX2__` se introdujeron en Visual Studio 2013 Update 2, versión 12.0.34567.1.  
  
 El optimizador elige cuándo y cómo se utilizan las instrucciones SSE y SSE2 cuando se especifica **\/arch**.  Usa las instrucciones de SSE y SSE2 para algunos cálculos escalares de punto flotante cuando determina que es más rápido utilizar las instrucciones y los registros de SSE y SSE2 en lugar de la pila de registros de punto flotante x87.  En consecuencia, el código podría utilizar realmente una combinación de x87 y SSE\/SSE2 para las operaciones de punto flotante.  Además, con **\/arch:SSE2**, se pueden utilizar instrucciones de SSE2 para algunas operaciones con enteros de 64 bits.  
  
 Además de utilizar las instrucciones de SSE y SSE2, el compilador también hace uso de otras instrucciones que se incluyen en las revisiones del procesador que admiten SSE y SSE2.  Un ejemplo es la instrucción CMOV, que apareció por primera vez en la revisión Pentium Pro de los procesadores Intel.  
  
 Dado que el compilador x86 genera código que utiliza instrucciones de SSE2 de forma predeterminada, debe especificar **\/arch:IA32** para deshabilitar la generación de las instrucciones de SSE y SSE2 para los procesadores x86.  
  
 **\/arch** solo afecta a la generación de código de las funciones nativas.  Cuando se usa [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **\/arch** no tiene ningún efecto en la generación de código para las funciones administradas.  
  
 **\/arch** y [\/QIfist](../../build/reference/qifist-suppress-ftol.md) no pueden utilizarse en la misma operación de compilación.  En particular, si no se utiliza `_controlfp` para modificar la palabra de control FP, el código de inicio en tiempo de ejecución establece el campo de control de precisión de la palabra de control FPU x87 en 53 bits.  Por consiguiente, cada operación de tipo float y double de una expresión usa un significado de 53 bits y un exponente de 15 bits.  Sin embargo, cada operación SSE de precisión sencilla utiliza significados de 24 bits y exponentes de 8 bits, mientras que las operaciones SSE2 de precisión doble utilizan significados de 53 bits y exponentes de 11 bits.  Para obtener más información, consulte [\_control87, \_controlfp, \_\_control87\_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md).  Estas diferencias son posibles en un árbol de expresión, pero no en los casos en los que se produce una asignación de usuario después de cada subexpresión.  Considere el siguiente caso:  
  
```c  
  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 Frente a:  
  
```c  
  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### Para establecer esta opción del compilador para AVX, AVX2, IA32, SSE o SSE2 en Visual Studio  
  
1.  Abra el cuadro de diálogo **Páginas de propiedades** del proyecto.  Para obtener más información, consulte [Cómo: Abrir páginas de propiedades del proyecto](../../misc/how-to-open-project-property-pages.md).  
  
2.  Elija la carpeta **Propiedades de configuración**, **C\/C\+\+**.  
  
3.  Seleccione la página de propiedades **Generación de código**.  
  
4.  Modifique la propiedad **Habilitar conjunto de instrucciones mejorado**.  
  
### Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## Vea también  
 [\/arch \(Arquitectura de CPU mínima\)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)