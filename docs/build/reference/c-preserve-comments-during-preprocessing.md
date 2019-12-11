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
ms.openlocfilehash: 6d0cf8e5f628f3f5301f54d7c853bfc2ab63cb7e
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988356"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conservar los comentarios durante el preprocesamiento)

Conserva los comentarios durante el preprocesamiento

## <a name="syntax"></a>Sintaxis

```
/C
```

## <a name="remarks"></a>Notas

Esta opción del compilador requiere la opción **/e**, **/p**o **/EP** .

En el ejemplo de código siguiente se mostrará el comentario del código fuente.

```cpp
// C_compiler_option.cpp
// compile with: /E /C /c
int i;   // a variable
```

Este ejemplo generará el siguiente resultado.

```
#line 1 "C_compiler_option.cpp"
int i;   // a variable
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades del **preprocesador** .

1. Modifique la propiedad **conservar comentarios** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/E (Preprocesar para stdout)](e-preprocess-to-stdout.md)<br/>
[/P (Preprocesar para archivo)](p-preprocess-to-a-file.md)<br/>
[/EP (Preprocesar para stdout sin directivas #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
