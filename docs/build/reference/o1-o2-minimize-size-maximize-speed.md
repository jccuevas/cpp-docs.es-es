---
title: -O1, - O2 (minimizar tamaño, maximizar velocidad) | Documentos de Microsoft
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /o2
- /o1
dev_langs:
- C++
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d6bbe16cb3f33e048c08d36cb9cd3d5016d7987c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimizar tamaño, maximizar velocidad)

Selecciona un conjunto predefinido de opciones que afectan al tamaño y la velocidad del código generado.

## <a name="syntax"></a>Sintaxis

> /O1  
> /O2

## <a name="remarks"></a>Comentarios

El **/O1** y **/O2** opciones del compilador son una manera rápida para establecer varias opciones de optimización específica a la vez. El **/O1** opción establece las opciones de optimización individuales que crea el código más pequeño en la mayoría de los casos. El **/O2** opción establece las opciones que crea el código más rápido en la mayoría de los casos. El **/O2** es la opción predeterminada para las versiones de lanzamiento. Esta tabla muestra las opciones específicas que se establezcan en **/O1** y **/O2**:

|Opción|Equivalente a|
|------------|-------------------|
|**/ O1** (minimizar tamaño)|[/ Og](../../build/reference/og-global-optimizations.md) [/Os](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GS](../../build/reference/gs-control-stack-checking-calls.md) [/GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|
|**/ O2** (maximizar velocidad)|[/ Og](../../build/reference/og-global-optimizations.md) [/Oi](../../build/reference/oi-generate-intrinsic-functions.md) [/Ot](../../build/reference/os-ot-favor-small-code-favor-fast-code.md) [/Oy](../../build/reference/oy-frame-pointer-omission.md) [/Ob2](../../build/reference/ob-inline-function-expansion.md) [/GS](../../build/reference/gs-control-stack-checking-calls.md)  [ /GF](../../build/reference/gf-eliminate-duplicate-strings.md) [/Gy](../../build/reference/gy-enable-function-level-linking.md)|

**/ O1** y **/O2** son mutuamente excluyentes.

> [!NOTE]  
> **x86 específico**  
> Estas opciones implican el uso de la omisión de puntero de marco ([/Oy](../../build/reference/oy-frame-pointer-omission.md)) opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. En **propiedades de configuración**, abra **C/C++** y, a continuación, elija la **optimización** página de propiedades.

1. Modificar el **optimización** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](../../build/reference/o-options-optimize-code.md)  
[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
[/EH (Modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md)