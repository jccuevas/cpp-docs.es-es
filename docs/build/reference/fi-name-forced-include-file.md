---
title: /FI (Dar nombre al archivo de inclusión obligatorio)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ForcedIncludes
- VC.Project.VCCLCompilerTool.ForcedIncludeFiles
- VC.Project.VCCLWCECompilerTool.ForcedIncludeFiles
- /fi
helpviewer_keywords:
- FI compiler option [C++]
- -FI compiler option [C++]
- /FI compiler option [C++]
- preprocess header file compiler option [C++]
ms.assetid: 07e79577-8152-4df9-a64c-aae08c603397
ms.openlocfilehash: e047ecc5266a898f2c6dc24be3c204f8ddf94386
ms.sourcegitcommit: 90817d9d78fbaed8ffacde63f3add334842e596f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/20/2019
ms.locfileid: "58278377"
---
# <a name="fi-name-forced-include-file"></a>/FI (Dar nombre al archivo de inclusión obligatorio)

Hace que el preprocesador procese el archivo de encabezado especificado.

## <a name="syntax"></a>Sintaxis

```
/FI[ ]pathname
```

## <a name="remarks"></a>Comentarios

Esta opción tiene el mismo efecto que especificar el archivo con comillas dobles en un `#include` la directiva en la primera línea de cada archivo de origen especificado en la línea de comandos en la variable de entorno de CL o en un archivo de comandos. Si utiliza varias **/FI** opciones, los archivos se incluyen en el orden en que se procesan cl.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **avanzadas** página de propiedades.

1. Modificar el **archivo de inclusión forzado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ForcedIncludeFiles%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
