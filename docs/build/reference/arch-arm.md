---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: b732a74d5fe223fdaf3b161d4ae92093ab5df407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295210"
---
# <a name="arch-arm"></a>/arch (ARM)

Especifica la arquitectura para la generación de código en ARM. Vea también [/arch (x86)](arch-x86.md) y [/arch (x64)](arch-x64.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Argumentos

**/arch:ARMv7VE**<br/>
Permite el uso de instrucciones de extensiones de virtualización de ARMv7VE.

**/arch:VFPv4**<br/>
Permite el uso de instrucciones VFPv4 de ARM. Si no se especifica esta opción, VFPv3 es el valor predeterminado.

## <a name="remarks"></a>Comentarios

El `_M_ARM_FP` macro (para ARM solo) indica que, si los hubiera, **/arch** usó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).

Cuando usas [/CLR](clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas. **/ arch** solo afecta a la generación de código para las funciones nativas.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Cómo establecer la opción del compilador /arch:ARMv7VE o /arch:VFPv4 en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue `/arch:ARMv7VE` o `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
