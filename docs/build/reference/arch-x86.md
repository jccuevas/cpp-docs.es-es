---
title: -arch (x86) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87e1826e324f8e544a791520a3ac035f5ab07100
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="arch-x86"></a>/arch (x86)
Especifica la arquitectura para la generación de código en x86. Consulte también [/arch (x64)](../../build/reference/arch-x64.md) y [/arch (ARM)](../../build/reference/arch-arm.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
/arch:[IA32|SSE|SSE2|AVX|AVX2]  
```  
  
## <a name="arguments"></a>Argumentos  
 **/arch:IA32**  
 No especifica ninguna instrucción mejorada y también especifica x87 para los cálculos de punto flotante.  
  
 **/ arch: SSE**  
 Habilita el uso de instrucciones SSE.  
  
 **/ arch: SSE2**  
 Habilita el uso de instrucciones SSE2. Se trata de la instrucción predeterminada en x86 plataformas si no hay ningún **/arch** se especifica la opción.  
  
 **/ arch: AVX**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.  
  
 **/arch:AVX2**  
 Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.  
  
## <a name="remarks"></a>Comentarios  
 Las instrucciones SSE2 y SSE existen en varios procesadores de AMD e Intel. Las instrucciones AVX existen en los procesadores Intel Sandy Bridge y AMD Bulldozer. Los procesadores Haswell y Broadwell de Intel y los procesadores basados en Excavator de AMD admiten las instrucciones AVX2.  
  
 El `_M_IX86_FP`, `__AVX__` y `__AVX2__` macros indican que, si existe, **/arch** se utilizó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). El **/arch:AVX2** opción y `__AVX2__` macro se introdujeron en Visual Studio 2013 Update 2, versión 12.0.34567.1.  
  
 El optimizador elige cuándo y cómo utilizar las instrucciones de SSE y SSE2 cuando **/arch** se especifica. Usa las instrucciones de SSE y SSE2 para algunos cálculos escalares de punto flotante cuando determina que es más rápido utilizar las instrucciones y los registros de SSE y SSE2 en lugar de la pila de registros de punto flotante x87. En consecuencia, el código podría utilizar realmente una combinación de x87 y SSE/SSE2 para las operaciones de punto flotante. Además, con **/arch: SSE2**, se pueden utilizar instrucciones de SSE2 para algunas operaciones con enteros de 64 bits.  
  
 Además de utilizar las instrucciones de SSE y SSE2, el compilador también hace uso de otras instrucciones que se incluyen en las revisiones del procesador que admiten SSE y SSE2. Un ejemplo es la instrucción CMOV, que apareció por primera vez en la revisión Pentium Pro de los procesadores Intel.  
  
 Puesto que la x86 compilador genera código que utiliza instrucciones de SSE2 de forma predeterminada, se debe especificar **/arch:IA32** para deshabilitar la generación de instrucciones de SSE y SSE2 para x86 procesadores.  
  
 **/ arch** solo afecta a la generación de código para las funciones nativas. Cuando usas [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas.  
  
 **/ arch** y [/QIfist](../../build/reference/qifist-suppress-ftol.md) no se puede usar en la misma operación de compilación. En particular, si no se utiliza `_controlfp` para modificar la palabra de control FP, el código de inicio en tiempo de ejecución establece el campo de control de precisión de la palabra de control FPU x87 en 53 bits. Por consiguiente, cada operación de tipo float y double de una expresión usa un significado de 53 bits y un exponente de 15 bits. Sin embargo, cada operación SSE de precisión sencilla utiliza significados de 24 bits y exponentes de 8 bits, mientras que las operaciones SSE2 de precisión doble utilizan significados de 53 bits y exponentes de 11 bits. Para obtener más información, vea [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md). Estas diferencias son posibles en un árbol de expresión, pero no en los casos en los que se produce una asignación de usuario después de cada subexpresión. Considere el siguiente caso:  
  
```cpp  
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.  
```  
  
 Comparar:  
  
```cpp  
t = f1 * f2;   // Do f1 * f2, round to the type of t.  
r = t + d;     // This should produce the same overall result   
               // whether x87 stack is used or SSE/SSE2 is used.  
```  
  
### <a name="to-set-this-compiler-option-for-avx-avx2-ia32-sse-or-sse2-in-visual-studio"></a>Para establecer esta opción del compilador para AVX, AVX2, IA32, SSE o SSE2 en Visual Studio  
  
1.  Abra la **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).  
  
2.  Seleccione el **propiedades de configuración**, **C/C++** carpeta.  
  
3.  Seleccione el **generación de código** página de propiedades.  
  
4.  Modificar el **Habilitar conjunto de instrucciones mejorado** propiedad.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación  
  
-   Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.  
  
## <a name="see-also"></a>Vea también  
 [/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)   
 [Opciones del compilador](../../build/reference/compiler-options.md)   
 [Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)