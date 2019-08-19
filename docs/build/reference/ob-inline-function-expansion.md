---
title: /Ob (Expansión de funciones inline)
ms.date: 08/08/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
helpviewer_keywords:
- inline functions, function expansion compiler option [C++]
- -Ob1 compiler option [C++]
- -Ob0 compiler option [C++]
- /Ob0 compiler option [C++]
- /Ob1 compiler option [C++]
- any suitable compiler option [C++]
- Ob2 compiler option [C++]
- Ob1 compiler option [C++]
- /Ob2 compiler option [C++]
- Ob compiler option [C++]
- -Ob2 compiler option [C++]
- disable compiler option [C++]
- -Ob compiler option [C++]
- /Ob compiler option [C++]
- only __inline compiler option [C++]
- Ob0 compiler option [C++]
- inline expansion, compiler option
ms.assetid: f134e6df-e939-4980-a01d-47425dbc562a
ms.openlocfilehash: 7eb3db1e359349eaf5125a6c8a46a3ac7d847f2f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915481"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Expansión de funciones inline)

Controla la expansión en línea de las funciones. De forma predeterminada, al optimizar, la expansión se produce a discreción del compilador en todas las funciones, lo que a menudo se conoce como *inserción automática*.

## <a name="syntax"></a>Sintaxis

::: moniker range=">=vs-2019"

> **/OB** {**0**|12|**3**}|

::: moniker-end

::: moniker range="<=vs-2017"

> **/OB** {**0**|12|}

::: moniker-end

## <a name="arguments"></a>Argumentos

**0,1**\
Valor predeterminado en [/OD](od-disable-debug.md). Deshabilita las expansiones en línea.

**1**\
Permite la expansión solo de las funciones marcadas como [inline](../../cpp/inline-functions-cpp.md), [__ inline](../../cpp/inline-functions-cpp.md) o [__forceinline](../../cpp/inline-functions-cpp.md), o en una función miembro C++ definida en una declaración de clase.

**dos**\
El valor predeterminado en [/O1](o1-o2-minimize-size-maximize-speed.md) y [/O2](o1-o2-minimize-size-maximize-speed.md). Permite al compilador expandir cualquier función no marcada explícitamente para ninguna inserción.

::: moniker range=">=vs-2019"

**3**\
Esta opción especifica una inclusión más agresiva que **/OB2**, pero tiene las mismas restricciones. La opción **/Ob3** está disponible a partir de Visual Studio 2019.

::: moniker-end

## <a name="remarks"></a>Comentarios

El compilador trata las opciones de expansión insertada y las palabras clave como sugerencias. No hay ninguna garantía de que ninguna función se expanda en línea. Puede deshabilitar las expansiones en línea, pero no puede forzar que el compilador inlinee una función determinada `__forceinline` , incluso cuando se usa la palabra clave.

Para excluir funciones de consideración como candidatas para la expansión en línea, puede usar [_ _ declspec (noinline)](../../cpp/noinline.md)o una región marcada por [#pragma auto_inline (OFF)](../../preprocessor/auto-inline.md) y las directivas [de auto_inline de #pragma (ON)](../../preprocessor/auto-inline.md) . Para obtener información sobre otra manera de proporcionar sugerencias de inclusión al compilador, vea la directiva [intrínseca #pragma](../../preprocessor/intrinsic.md) .

> [!NOTE]
> La información que se recopila a partir de las ejecuciones de pruebas de generación de perfiles invalida las optimizaciones que, de otro modo, estarían en vigor porque especificó **/OB**, **/os**o **/OT**. Para más información, vea [Optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de **propiedades** > configuración de > **C/C++** **optimización** .

1. Modifique la propiedad expansión de la **función insertada** .

::: moniker range=">=vs-2019"

La opción **/Ob3** no está disponible en la propiedad de expansión de la **función insertada** . Para establecer **/Ob3**:

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de **propiedades propiedades** > de > configuración **CC++ /** **línea de comandos** .

1. Escriba **/Ob3** en **opciones adicionales**.

::: moniker-end

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Vea también

[/O (opciones) (optimizar código)](o-options-optimize-code.md)\
[Opciones del compilador MSVC](compiler-options.md)\
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
