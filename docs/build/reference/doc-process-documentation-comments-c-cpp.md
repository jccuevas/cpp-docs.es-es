---
title: -doc (procesar comentarios de documentación) (C/C ++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.GenerateXMLDocumentationFiles
- /doc
- VC.Project.VCCLCompilerTool.XMLDocumentationFileName
dev_langs:
- C++
helpviewer_keywords:
- /doc compiler option [C++]
- comments, C++ code
- XML documentation, comments in source files
- -doc compiler option [C++]
ms.assetid: b54f7e2c-f28f-4f46-9ed6-0db09be2cc63
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 488ee353cf245303b5ea73be139a262aea5be49d
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45706581"
---
# <a name="doc-process-documentation-comments-cc"></a>/doc (Procesar comentarios de documentación) (C/C++)

Hace que el compilador para procesar los comentarios de documentación en archivos de código fuente y para crear un archivo .xdc para cada archivo de código fuente que tenga comentarios de documentación.

## <a name="syntax"></a>Sintaxis

> **/ doc**[*nombre*]

## <a name="arguments"></a>Argumentos

*name*<br/>
El nombre del archivo .xdc que va a crear el compilador. Solo es válido cuando se pasa un archivo .cpp en la compilación.

## <a name="remarks"></a>Comentarios

Los archivos .xdc se procesan en un archivo .xml con xdcmake.exe. Para obtener más información, consulte [referencia de XDCMake](../../ide/xdcmake-reference.md).

Puede agregar comentarios de documentación para los archivos de código fuente. Para obtener más información, consulte [etiquetas recomendadas para comentarios de documentación](../../ide/recommended-tags-for-documentation-comments-visual-cpp.md).

Para usar el archivo .xml generado con IntelliSense, hacer que el nombre de archivo del archivo .xml igual que el ensamblado que desea admitir y ponga el archivo .xml se encuentra en el mismo directorio que el ensamblado. Cuando se hace referencia al ensamblado en el proyecto de Visual Studio, también se encuentra el archivo .xml. Para obtener más información, consulte [Using IntelliSense](/visualstudio/ide/using-intellisense) y [proporcionar comentarios del código XML](/visualstudio/ide/supplying-xml-code-comments).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **archivos de salida** página de propiedades.

1. Modificar el **generar archivos de documentación XML** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.GenerateXMLDocumentationFiles%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)