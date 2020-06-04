---
title: /GX (Habilitar el control de excepciones)
ms.date: 11/19/2019
f1_keywords:
- /gx
helpviewer_keywords:
- exception handling, enabling
- /GX compiler option [C++]
- -GX compiler option [C++]
- cl.exe compiler, exception handling
- enable exception handling compiler option [C++]
- GX compiler option [C++]
ms.assetid: 933b43ba-de77-4ff8-a48b-7074de90bc1c
ms.openlocfilehash: 171ff0d0dfb1dec41bae5f6be63c941802c402a4
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245085"
---
# <a name="gx-enable-exception-handling"></a>/GX (Habilitar el control de excepciones)

Opción obsoleta. Habilita el control de excepciones sincrónicas mediante la suposición de que las funciones declaradas mediante `extern "C"` nunca producen una excepción.

## <a name="syntax"></a>Sintaxis

```
/GX
```

## <a name="remarks"></a>Comentarios

**/GX** está en desuso. En su lugar, use la opción de [/EHsc](eh-exception-handling-model.md) equivalente. Para obtener una lista de opciones del compilador en desuso, vea la sección Opciones del compilador en **desuso y quitadas** en [las opciones del compilador enumeradas por categoría](compiler-options-listed-by-category.md).

De forma predeterminada, **/EHsc**, el equivalente de **/GX**, está en vigor al compilar con el entorno de desarrollo de Visual Studio. Cuando se usan las herramientas de línea de comandos, no se especifica ningún control de excepciones. Es el equivalente de **/GX-** .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. En el panel de navegación, seleccione **propiedades de configuración**, **CC++/** , línea de **comandos**.

1. Escriba la opción del compilador en el cuadro **Opciones adicionales** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/EH (Modelo de control de excepciones)](eh-exception-handling-model.md)
