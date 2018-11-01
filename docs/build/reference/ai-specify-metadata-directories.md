---
title: /AI (Especificar directorios de metadatos)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.AdditionalUsingDirectories
- VC.Project.VCNMakeTool.AssemblySearchPath
- /AI
- VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories
helpviewer_keywords:
- /AI compiler option [C++]
- AI compiler option [C++]
- -AI compiler option [C++]
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
ms.openlocfilehash: a9e752f68ed53c7a94fec1914bc42c39a17648b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471532"
---
# <a name="ai-specify-metadata-directories"></a>/AI (Especificar directorios de metadatos)

Especifica un directorio en el que el compilador debe buscar para resolver las referencias de archivos que se pasan a la directiva `#using`.

## <a name="syntax"></a>Sintaxis

> **/AI**_directorio_

## <a name="arguments"></a>Argumentos

*Directorio*<br/>
Directorio o ruta de acceso donde debe buscar el compilador.

## <a name="remarks"></a>Comentarios

Un único directorio puede pasarse a una **/AI** invocación. Especifique uno **/AI** opción para cada ruta de acceso que desea que el compilador para buscar. Por ejemplo, para agregar C:\Project\Meta y C:\Common\Meta a la ruta de acceso de búsqueda del compilador para `#using` directivas, agregue `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` a la línea de comandos del compilador o agregue cada directorio a la **adicionales # directorios using** propiedad en Visual Studio.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **General** página de propiedades.

1. Modificar el **adicionales # directorios using** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[#using (directiva)](../../preprocessor/hash-using-directive-cpp.md)
