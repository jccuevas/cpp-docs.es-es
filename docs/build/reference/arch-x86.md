---
title: /arch (x86)
ms.date: 11/04/2016
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: e2aba6dc18db621710b5293f9f970fa5f453b8a9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421812"
---
# <a name="arch-x86"></a>/arch (x86)

Especifica la arquitectura para la generación de código en x86. Consulte también [/arch (x64)](../../build/reference/arch-x64.md) y [/arch (ARM)](../../build/reference/arch-arm.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[IA32|SSE|SSE2|AVX|AVX2]
```

## <a name="arguments"></a>Argumentos

**/arch:IA32**<br/>
No especifica ninguna instrucción mejorada y también especifica x87 para los cálculos de punto flotante.

**/arch:SSE**<br/>
Habilita el uso de instrucciones SSE.

**/arch:SSE2**<br/>
Habilita el uso de instrucciones SSE2. Se trata de la instrucción predeterminada en x86 plataformas si no hay ningún **/arch** se especifica la opción.

**/arch:AVX**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.

**/arch:AVX2**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.

## <a name="remarks"></a>Comentarios

Las instrucciones SSE2 y SSE existen en varios procesadores de AMD e Intel. Las instrucciones AVX existen en los procesadores Intel Sandy Bridge y AMD Bulldozer. Los procesadores Haswell y Broadwell de Intel y los procesadores basados en Excavator de AMD admiten las instrucciones AVX2.

El `_M_IX86_FP`, `__AVX__` y `__AVX2__` macros indican que, si los hubiera, **/arch** usó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). El **/arch: avx2** opción y `__AVX2__` macro se introdujeron en Visual Studio 2013 Update 2, versión 12.0.34567.1.

El optimizador elige cuándo y cómo usar las instrucciones de SSE y SSE2 cuando **/arch** se especifica. Usa las instrucciones de SSE y SSE2 para algunos cálculos escalares de punto flotante cuando determina que es más rápido utilizar las instrucciones y los registros de SSE y SSE2 en lugar de la pila de registros de punto flotante x87. En consecuencia, el código podría utilizar realmente una combinación de x87 y SSE/SSE2 para las operaciones de punto flotante. Además, con **/arch: SSE2**, se pueden usar instrucciones de SSE2 para algunas operaciones con enteros de 64 bits.

Además de utilizar las instrucciones de SSE y SSE2, el compilador también hace uso de otras instrucciones que se incluyen en las revisiones del procesador que admiten SSE y SSE2. Un ejemplo es la instrucción CMOV, que apareció por primera vez en la revisión Pentium Pro de los procesadores Intel.

Dado que el x86 compilador genera código que usa las instrucciones SSE2 de forma predeterminada, debe especificar **/arch: IA32** para deshabilitar la generación de instrucciones SSE y SSE2 para x86 procesadores.

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

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración**, **C o C++** carpeta.

1. Seleccione el **generación de código** página de propiedades.

1. Modificar el **Habilitar conjunto de instrucciones mejorado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
