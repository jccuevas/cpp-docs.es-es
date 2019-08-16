---
title: /O1, /O2 (Minimizar tamaño, maximizar velocidad)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
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
ms.openlocfilehash: d33fe6bceae09267fd3f79ffe3dc26864e87c764
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320362"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimizar tamaño, maximizar velocidad)

Selecciona un conjunto predefinido de opciones que afectan al tamaño y la velocidad del código generado.

## <a name="syntax"></a>Sintaxis

> / / O2 O1

## <a name="remarks"></a>Comentarios

El **/O1** y **/O2** opciones del compilador son una forma rápida para establecer varias opciones de optimización específicas a la vez. El **/O1** opción establece las opciones de optimización individual que crea el código más pequeño en la mayoría de los casos. El **/O2** opción establece las opciones que crea el código más rápido en la mayoría de los casos. El **/O2** es la opción predeterminada para las compilaciones de versión. Esta tabla muestran las opciones específicas que se establezcan en **/O1** y **/O2**:

|Opción|Equivalente a|
|------------|-------------------|
|**/ O1** (minimizar tamaño)|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/ O2** (maximizar velocidad)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/Ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/ O1** y **/O2** son mutuamente excluyentes.

> [!NOTE]
> **x86 específico** estas opciones implican el uso de la omisión de puntero de marco ([/Oy](oy-frame-pointer-omission.md)) opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. En **propiedades de configuración**, abra **C o C++** y, a continuación, elija el **optimización** página de propiedades.

1. Modificar el **optimización** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Modelo de control de excepciones)](eh-exception-handling-model.md)
