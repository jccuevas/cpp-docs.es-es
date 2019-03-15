---
title: /FR, /Fr (Crear archivo .Sbr)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.BrowseInformation
- VC.Project.VCCLCompilerTool.BrowseInformation
- /fr
- VC.Project.VCCLCompilerTool.BrowseInformationFile
- VC.Project.VCCLWCECompilerTool.BrowseInformationFile
helpviewer_keywords:
- /FR compiler option [C++]
- -FR compiler option [C++]
- FR compiler option [C++]
- symbolic browser information
ms.assetid: 3fd8f88b-3924-4feb-9393-287036a28896
ms.openlocfilehash: a75a9d143012dee7946591d708921d6734b2acda
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811880"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Crear archivo .Sbr)

Crea archivos. sbr.

## <a name="syntax"></a>Sintaxis

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Comentarios

Durante el proceso de compilación, la Utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE) usa estos archivos para crear un archivo .BSC, que se usa para mostrar la información del examen.

**/FR** crea un archivo .sbr con información simbólica completa.

**/Fr** crea un archivo .sbr sin información sobre variables locales.

Si no se especifica el valor de `filename`, el archivo .sbr recibe el mismo nombre base que el archivo de origen.

**/Fr** está en desuso. Use **/FR** en su lugar. Para obtener más información, consulte Opciones de compilador en desuso y quitadas en [Compiler Options Listed by Category](compiler-options-listed-by-category.md).

> [!NOTE]
>  No cambie la extensión. sbr. BSCMAKE requiere esta extensión en los archivos intermedios.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. En el panel de navegación, elija **C o C++** y, a continuación, página de propiedades **Información de examen** .

1. Modifique el **Archivo de información de examen** o la propiedad **Habilitar información de examen** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
