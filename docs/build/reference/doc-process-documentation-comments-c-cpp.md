---
title: /doc (Procesar comentarios de documentación) (C/C++)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
ms.openlocfilehash: 90f63a972245114424b64d4131420dcb4e1e925a
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342908"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Procesar comentarios de documentación) (C/C++)

Hace que el compilador para procesar los comentarios de documentación en archivos de código fuente y para crear un archivo .xdc para cada archivo de código fuente que tenga comentarios de documentación.

## <a name="syntax"></a>Sintaxis

> **/doc**[*name*]

## <a name="arguments"></a>Argumentos

*name*<br/>
El nombre del archivo .xdc que va a crear el compilador. Solo es válido cuando se pasa un archivo .cpp en la compilación.

## <a name="remarks"></a>Comentarios

Los archivos .xdc se procesan en un archivo .xml con xdcmake.exe. Para obtener más información, consulte [referencia de XDCMake](xdcmake-reference.md).

Puede agregar comentarios de documentación para los archivos de código fuente. Para más información, consulte [Etiquetas recomendadas para los comentarios de documentación](recommended-tags-for-documentation-comments-visual-cpp.md).

Para usar el archivo .xml generado con IntelliSense, hacer que el nombre de archivo del archivo .xml igual que el ensamblado que desea admitir y ponga el archivo .xml se encuentra en el mismo directorio que el ensamblado. Cuando se hace referencia al ensamblado en el proyecto de Visual Studio, también se encuentra el archivo .xml. Para obtener más información, consulte [Using IntelliSense](/visualstudio/ide/using-intellisense) y [proporcionar comentarios del código XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **archivos de salida** página de propiedades.

1. Modificar el **generar archivos de documentación XML** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
