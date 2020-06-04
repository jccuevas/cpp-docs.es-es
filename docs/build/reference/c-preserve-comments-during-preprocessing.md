---
title: /C (Conservar los comentarios durante el preprocesamiento)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.KeepComments
- VC.Project.VCCLWCECompilerTool.KeepComments
helpviewer_keywords:
- comments, not stripping during preprocessing
- preserve comments during preprocessing
- -c compiler option [C++]
- c compiler option [C++]
- /c compiler option [C++]
ms.assetid: 944567ca-16bc-4728-befe-d414a7787f26
ms.openlocfilehash: f80ebf45dd396a3f92d9b755c56522d4731bb2d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440277"
---
# <a name="c-preserve-comments-during-preprocessing"></a>/C (Conservar los comentarios durante el preprocesamiento)

Conserva los comentarios durante el preprocesamiento

## <a name="syntax"></a>Sintaxis

```
/C
```

## <a name="remarks"></a>Observaciones

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

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/E (Preprocesar para stdout)](e-preprocess-to-stdout.md)<br/>
[/P (Preprocesar para archivo)](p-preprocess-to-a-file.md)<br/>
[/EP (Preprocesar para stdout sin directivas #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
