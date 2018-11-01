---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: bf12abd140a56b1b914156083ecbbd3e61e7285a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495588"
---
# <a name="arch-arm"></a>/arch (ARM)

Especifica la arquitectura para la generación de código en ARM. Vea también [/arch (x86)](../../build/reference/arch-x86.md) y [/arch (x64)](../../build/reference/arch-x64.md).

## <a name="syntax"></a>Sintaxis

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>Argumentos

**armv7ve**<br/>
Permite el uso de instrucciones de extensiones de virtualización de ARMv7VE.

**/arch:VFPv4**<br/>
Permite el uso de instrucciones VFPv4 de ARM. Si no se especifica esta opción, VFPv3 es el valor predeterminado.

## <a name="remarks"></a>Comentarios

El `_M_ARM_FP` macro (para ARM solo) indica que, si los hubiera, **/arch** usó la opción del compilador. Para obtener más información, consulta [Predefined Macros](../../preprocessor/predefined-macros.md).

Cuando usas [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) para compilar, **/arch** no tiene ningún efecto sobre la generación de código para las funciones administradas. **/ arch** solo afecta a la generación de código para las funciones nativas.

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Cómo establecer la opción del compilador /arch:ARMv7VE o /arch:VFPv4 en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. En el **opciones adicionales** , agregue `/arch:ARMv7VE` o `/arch:VFPv4`.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>.

## <a name="see-also"></a>Vea también

[/arch (Arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)