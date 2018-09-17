---
title: -arch (ARM) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 17f0f0735981c0a851bcab62ca1ad39c97af3965
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45700689"
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

[/arch (arquitectura de CPU mínima)](../../build/reference/arch-minimum-cpu-architecture.md)
[opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)