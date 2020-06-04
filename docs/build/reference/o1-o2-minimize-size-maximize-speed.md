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
ms.openlocfilehash: 3daf5dd5f9912194fd5d8aaeb4c7a312be142b69
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825355"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1, /O2 (Minimizar tamaño, maximizar velocidad)

Selecciona un conjunto predefinido de opciones que afectan al tamaño y a la velocidad del código generado.

## <a name="syntax"></a>Sintaxis

> O1
> /O2

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/O1** y **/O2** son una forma rápida de establecer varias opciones de optimización específicas a la vez. La opción **/O1** establece las opciones de optimización individuales que crean el código más pequeño en la mayoría de los casos. La opción **/O2** establece las opciones que crean el código más rápido en la mayoría de los casos. La opción **/O2** es el valor predeterminado para las compilaciones de versión. En esta tabla se muestran las opciones específicas establecidas por **/O1** y **/O2**:

|Opción|Equivalente a|
|------------|-------------------|
|**/O1** (minimizar tamaño)|[/Og](og-global-optimizations.md) [/os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/OB2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/GY](gy-enable-function-level-linking.md)|
|**/O2** (maximizar velocidad)|[/Og](og-global-optimizations.md) [/OI](oi-generate-intrinsic-functions.md) [/OT](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/OB2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/GY](gy-enable-function-level-linking.md)|

**/O1** y **/O2** se excluyen mutuamente.

> [!NOTE]
> **Específico de x86**\
> Estas opciones implican el uso de la opción de omisión de puntero de marco ([/Oy](oy-frame-pointer-omission.md)).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. En **propiedades de configuración**, Abra **C/C++** y, a continuación, elija la página de propiedades **optimización** .

1. Modifique la propiedad **optimización** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>.

## <a name="see-also"></a>Consulte también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Modelo de control de excepciones)](eh-exception-handling-model.md)
