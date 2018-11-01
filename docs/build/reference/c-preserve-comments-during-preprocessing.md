---
title: /C (Conservar los comentarios durante el preprocesamiento)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- /c
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: b37e279af3995bd1d61c97dc88b49cdd95495c75
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442606"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conservar los comentarios durante el preprocesamiento)

Conserva los comentarios durante el preprocesamiento

## <a name="syntax"></a>Sintaxis

```
/C
```

## <a name="remarks"></a>Comentarios

Esta opción del compilador requiere la **/E**, **/P**, o **/EP** opción.

El siguiente ejemplo de código mostrará el comentario de código fuente.

```
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Este ejemplo genera el siguiente resultado.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **preprocesador** página de propiedades.

1. Modificar el **mantener comentarios** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/E (Preprocesar para stdout)](../../build/reference/e-preprocess-to-stdout.md)<br/>
[/P (Preprocesar para archivo)](../../build/reference/p-preprocess-to-a-file.md)<br/>
[/EP (Preprocesar para stdout sin directivas #line)](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)