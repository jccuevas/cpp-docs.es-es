---
title: -Ob (expansión de funciones Inline) | Microsoft Docs
ms.custom: ''
ms.date: 09/25/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.InlineFunctionExpansion
- VC.Project.VCCLCompilerTool.InlineFunctionExpansion
- /ob
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43c67e4919680167bdde5e9f8ad9426229956fad
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401997"
---
# <a name="ob-inline-function-expansion"></a>/Ob (Expansión de funciones inline)

Controla la expansión en línea de las funciones.

## <a name="syntax"></a>Sintaxis

> /OB {0 | 1 | 2}

## <a name="arguments"></a>Argumentos

**0**<br/>
Deshabilita las expansiones en línea. De forma predeterminada, expansión se produce a discreción del compilador en todas las funciones, suele denominarse *inline automático*.

**1**<br/>
Permite la expansión solo de las funciones marcadas como [inline](../../cpp/inline-functions-cpp.md), `__inline`, o `__forceinline`, o en una función de miembro de C++ definidas en una declaración de clase.

**2**<br/>
Valor predeterminado. Permite la expansión de las funciones marcadas como `inline`, `__inline` o `__forceinline` y de cualquier otra función que elija el compilador.

**/ Ob2** cuando [/O1, / O2 (minimizar tamaño, maximizar velocidad)](../../build/reference/o1-o2-minimize-size-maximize-speed.md) o [/Ox (habilitar más las optimizaciones de velocidad)](../../build/reference/ox-full-optimization.md) se utiliza.

Esta opción requiere que habilite las optimizaciones mediante **/O1**, **/O2**, **/Ox**, o **/Og**.

## <a name="remarks"></a>Comentarios

El compilador trata las opciones de expansión insertada y las palabras clave como sugerencias. No hay ninguna garantía de que las funciones es expandan en línea. Puede deshabilitar las expansiones en línea, pero no se puede forzar al compilador a que inserte una función determinada, incluso cuando se usa la palabra clave `__forceinline`.

Puede usar el `#pragma` [auto_inline](../../preprocessor/auto-inline.md) directiva para excluir funciones de considerarse candidatas para la expansión en línea. Consulte también el `#pragma` [intrínseco](../../preprocessor/intrinsic.md) directiva.

> [!NOTE]
> Información recopilada de ejecuciones de pruebas de generación de perfiles reemplazará las optimizaciones que en caso contrario, estarían activas si se especifica **/Ob**, **/Os**, o **/Ot**. Para obtener más información, consulte [optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda **propiedades de configuración**, **C o C++** y seleccione **optimización**.

1. Modificar el **expansión de funciones insertadas** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.InlineFunctionExpansion%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](../../build/reference/o-options-optimize-code.md)<br/>
[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)