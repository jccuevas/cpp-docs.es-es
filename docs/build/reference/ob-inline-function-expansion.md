---
title: /Ob (Expansión de funciones inline)
ms.date: 09/25/2017
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
ms.openlocfilehash: 6bf16e5725916e81e64d80c0a1f96bf502c8826c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57807526"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Expansión de funciones inline)

Controla la expansión en línea de las funciones.

## <a name="syntax"></a>Sintaxis

> /Ob{0|1|2}

## <a name="arguments"></a>Argumentos

**0**<br/>
Deshabilita las expansiones en línea. De forma predeterminada, expansión se produce a discreción del compilador en todas las funciones, suele denominarse *inline automático*.

**1**<br/>
Permite la expansión solo de las funciones marcadas como [inline](../../cpp/inline-functions-cpp.md), `__inline`, o `__forceinline`, o en una función de miembro de C++ definidas en una declaración de clase.

**2**<br/>
Valor predeterminado. Permite la expansión de las funciones marcadas como `inline`, `__inline` o `__forceinline` y de cualquier otra función que elija el compilador.

**/ Ob2** cuando [/O1, / O2 (minimizar tamaño, maximizar velocidad)](o1-o2-minimize-size-maximize-speed.md) o [/Ox (habilitar más las optimizaciones de velocidad)](ox-full-optimization.md) se utiliza.

Esta opción requiere que habilite las optimizaciones mediante **/O1**, **/O2**, **/Ox**, o **/Og**.

## <a name="remarks"></a>Comentarios

El compilador trata las opciones de expansión insertada y las palabras clave como sugerencias. No hay ninguna garantía de que las funciones es expandan en línea. Puede deshabilitar las expansiones en línea, pero no se puede forzar al compilador a que inserte una función determinada, incluso cuando se usa la palabra clave `__forceinline`.

Puede usar el `#pragma` [auto_inline](../../preprocessor/auto-inline.md) directiva para excluir funciones de considerarse candidatas para la expansión en línea. Consulte también el `#pragma` [intrínseco](../../preprocessor/intrinsic.md) directiva.

> [!NOTE]
> Información recopilada de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, consulte [optimizaciones guiadas por perfiles](../profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda **propiedades de configuración**, **C o C++** y seleccione **optimización**.

1. Modificar el **expansión de funciones insertadas** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
