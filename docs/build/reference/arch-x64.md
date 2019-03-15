---
title: /arch (x64)
ms.date: 11/04/2016
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: c515307ee3a49ef746eea939e90d7aecbd661b95
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809319"
---
# <a name="arch-x64"></a>/arch (x64)

Especifica la arquitectura para la generación de código en x64. Consulte también [/arch (x86)](arch-x86.md) y [/arch (ARM)](arch-arm.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[AVX|AVX2]
```

## <a name="arguments"></a>Argumentos

**/arch:AVX**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas de Intel.

**/arch:AVX2**<br/>
Habilita el uso de instrucciones de Extensiones de vector avanzadas 2 (AVX2) de Intel.

## <a name="remarks"></a>Comentarios

**/ arch** solo afecta a la generación de código para las funciones nativas. Cuando usas [/CLR](clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas.

El `__AVX__` se define el símbolo de preprocesador cuando la **/arch: AVX** se especificó la opción del compilador. El `__AVX2__` se define el símbolo de preprocesador cuando la **/arch: avx2** se especificó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md). El **/arch: avx2** opción se introdujo en Visual Studio 2013 Update 2, versión 12.0.34567.1.

### <a name="to-set-the-archavx-or-archavx2-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /arch:AVX o /arch:AVX2 en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración**, **C o C++** carpeta.

1. Seleccione el **generación de código** página de propiedades.

1. En el **Habilitar conjunto de instrucciones mejorado** lista desplegable, seleccione **extensiones de Vector avanzadas (/ arch: AVX)** o **extensiones de Vector avanzadas 2 (/ arch: AVX2)**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
