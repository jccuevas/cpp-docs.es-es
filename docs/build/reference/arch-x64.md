---
title: /arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 0ade6d9f744339ebaf38981d81334340b56080cb
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816222"
---
# <a name="arch-x64"></a>/arch (x64)

Especifica la arquitectura para la generación de código en x64. Consulte también [/Arch (x86)](arch-x86.md) y [/Arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>Argumentos

**/arch:AVX**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.

**/arch:AVX2**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.

**/Arch: AVX512**<br/>
Habilita el uso de las instrucciones de las extensiones de vector avanzadas de Intel 512.

## <a name="remarks"></a>Comentarios

La opción **/Arch** habilita el uso de determinadas extensiones de conjunto de instrucciones, especialmente para el cálculo de vectores, disponibles en procesadores de Intel y AMD. En general, los procesadores que se introdujeron más recientemente pueden admitir extensiones adicionales sobre las que admiten procesadores anteriores, aunque debe consultar la documentación de un procesador determinado o probar la compatibilidad con la extensión del conjunto de instrucciones mediante [_ _ CPUID](../../intrinsics/cpuid-cpuidex.md) antes de ejecutar código mediante una extensión de conjunto de instrucciones.

**/Arch** solo afecta a la generación de código para las funciones nativas. Cuando se usa [/CLR](clr-common-language-runtime-compilation.md) para compilar, **/Arch** no tiene ningún efecto en la generación de código para las funciones administradas.

Las extensiones de procesador tienen las siguientes características:

- El modo predeterminado usa instrucciones SSE2 para los cálculos de punto flotante y de vectores escalares. Estas instrucciones permiten el cálculo con vectores de 128 bits de valores enteros de precisión sencilla, doble precisión y 1, 2, 4 u 8 bytes, así como valores de punto flotante de precisión sencilla y de doble precisión.

- **AVX** presentó una codificación de instrucciones alternativa para las instrucciones escalares de vectores y puntos flotantes que permite vectores de 128 bits o 256 bits, y ceros extiende todos los resultados vectoriales al tamaño del vector completo. (Para compatibilidad heredada, las instrucciones de vector de estilo SSE conservan todos los bits más allá del bit 127). La mayoría de las operaciones de punto flotante se extienden a 256 bits.

- **AVX2** extiende la mayoría de las operaciones de enteros a vectores de 256 bits y permite el uso de instrucciones de multiplicación y adición fusionadas (FMA).

- **AVX-512** presentó otro formulario de codificación de instrucciones que permite vectores de 512 bits, además de otras características opcionales. También se han agregado instrucciones para operaciones adicionales.

Cada opción **/Arch** también puede habilitar el uso de otras instrucciones no vectoriales asociadas a esa opción. Un ejemplo es el uso de ciertas instrucciones de IMC cuando se especifica **/Arch: AVX2** .

El símbolo de preprocesador `__AVX__` se define cuando se especifica la opción del compilador **/Arch: AVX**, **/Arch: AVX2** o **/Arch: AVX512** . El símbolo de preprocesador `__AVX2__` se define cuando se especifica la opción del compilador **/Arch: AVX2** o **/Arch: AVX512** . Los símbolos de preprocesador `__AVX512F__`, `__AVX512CD__`, `__AVX512BW__`, `__AVX512DQ__` y `__AVX512VL__` se definen cuando se especifica la opción del compilador **/Arch: AVX512** . Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). La opción **/Arch: AVX2** se presentó en Visual Studio 2013 Update 2, versión 12.0.34567.1. La compatibilidad limitada con **/Arch: AVX512** se agregó en visual Studio 2017 y se amplió en visual Studio 2019.

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador/Arch: AVX,/Arch: AVX2 o/Arch: AVX512 en Visual Studio

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la carpeta **propiedades de configuración**, **C/C++**  .

1. Seleccione la página de propiedades **generación de código** .

1. En el cuadro desplegable **Habilitar conjunto de instrucciones mejorado** , elija **extensiones de vector avanzadas (/Arch: AVX)** , **extensiones de vector avanzadas 2 (/Arch: AVX2)** o **extensiones de vector avanzadas 512 (/Arch: AVX512)** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
