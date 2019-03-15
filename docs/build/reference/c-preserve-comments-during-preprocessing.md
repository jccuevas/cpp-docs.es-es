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
ms.openlocfilehash: c5854fd1255ab509d8778828de25638dd821d74b
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57821448"
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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **preprocesador** página de propiedades.

1. Modificar el **mantener comentarios** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.KeepComments%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/E (Preprocesar para stdout)](e-preprocess-to-stdout.md)<br/>
[/P (Preprocesar para archivo)](p-preprocess-to-a-file.md)<br/>
[/EP (Preprocesar para stdout sin directivas #line)](ep-preprocess-to-stdout-without-hash-line-directives.md)
