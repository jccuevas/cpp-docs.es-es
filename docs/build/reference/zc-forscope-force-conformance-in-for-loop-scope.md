---
title: '/ Zc: forScope (Forzar ajuste en el ámbito del bucle for) | Documentos de Microsoft'
ms.custom: ''
ms.date: 03/06/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.ForceConformanceInForLoopScope
- VC.Project.VCCLWCECompilerTool.ForceConformanceInForLoopScope
- /zc:forScope
dev_langs:
- C++
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: 3031f02d-3b14-4ad0-869e-22b0110c3aed
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b21c844cd29c7fb45e58f44fdf8eaae427b74235
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378618"
---
# <a name="zcforscope-force-conformance-in-for-loop-scope"></a>/Zc:forScope (Forzar ajuste en el ámbito del bucle For)

Se usa para implementar el comportamiento estándar de C++ de los bucles [for](../../cpp/for-statement-cpp.md) con las extensiones de Microsoft ([/Ze](../../build/reference/za-ze-disable-language-extensions.md)).

## <a name="syntax"></a>Sintaxis

> **/ Zc: forScope**[**-**]

## <a name="remarks"></a>Comentarios

El comportamiento estándar consiste en dejar que el inicializador de un bucle **for** salga del ámbito después del bucle **for** . En **/Zc:forScope-** y [/Ze](../../build/reference/za-ze-disable-language-extensions.md), el inicializador del bucle **for** permanece dentro del ámbito hasta que finaliza el ámbito local.

El **/Zc: forScope** opción está activada de forma predeterminada. **/ Zc: forScope** no se ve afectado cuando el [/ permisivo-](permissive-standards-conformance.md) se especifica la opción.

La opción **/Zc:forScope-** está en desuso y se quitará en una próxima versión. El uso de **/Zc:forScope-** genera la advertencia de elemento en desuso D9035.

El siguiente código se compila en **/Ze** , pero no en **/Za**:

```cpp
// zc_forScope.cpp
// compile by using: cl /Zc:forScope- /Za zc_forScope.cpp
// C2065, D9035 expected  
int main() {
    // Compile by using cl /Zc:forScope- zc_forScope.cpp
    // to compile this non-standard code as-is.
    // Uncomment the following line to resolve C2065 for /Za.
    // int i;
    for (int i = 0; i < 1; i++)
        ;
    i = 20;   // i has already gone out of scope under /Za
}
```

Si usa **/Zc:forScope-**, se generará una advertencia C4288 (desactivada de forma predeterminada) si una variable está dentro del ámbito debido a una declaración que se realizó en un ámbito anterior. Para mostrarlo, quite los caracteres `//` del código de ejemplo para declarar `int i`.

Puede modificar el comportamiento en tiempo de ejecución de **/Zc:forScope** mediante la pragma [conform](../../preprocessor/conform.md) .

Si usa **/Zc:forScope-** en un proyecto con un archivo .pch existente, se genera una advertencia, se ignora **/Zc:forScope-** y la compilación continúa con los archivos .pch existentes. Si desea que genere un nuevo archivo .pch, use [/Yc (crear archivo de encabezado precompilado)](../../build/reference/yc-create-precompiled-header-file.md).

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **lenguaje** página de propiedades.

1. Modifique la propiedad **Forzar ajuste en el ámbito del bucle For** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForceConformanceInForLoopScope%2A>.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
[/Za, /Ze (Deshabilitar extensiones de lenguaje)](../../build/reference/za-ze-disable-language-extensions.md)<br/>
