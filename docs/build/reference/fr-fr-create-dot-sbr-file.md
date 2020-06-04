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
ms.openlocfilehash: 58f55811f5d2bb81bc77da38a87c35bae91ce6cb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320518"
---
# <a name="fr-fr-create-sbr-file"></a>/FR, /Fr (Crear archivo .Sbr)

Crea archivos. sbr.

## <a name="syntax"></a>Sintaxis

```
/FR[pathname[\filename]]
/Fr[pathname[\filename]]
```

## <a name="remarks"></a>Observaciones

> [!WARNING]
> Aunque BSCMAKE todavía se instala con Visual Studio, el IDE ya no lo utiliza. Desde Visual Studio 2008, la información de examen y de símbolos se almacena automáticamente en un archivo .sdf de SQL Server en la carpeta de soluciones.

Durante el proceso de compilación, la Utilidad de mantenimiento de información de examen de Microsoft (BSCMAKE) usa estos archivos para crear un archivo .BSC, que se usa para mostrar la información del examen.

**/FR** crea un archivo .sbr con información simbólica completa.

**/Fr** crea un archivo .sbr sin información sobre variables locales.

Si no se especifica el valor de `filename`, el archivo .sbr recibe el mismo nombre base que el archivo de origen.

**/Fr** está en desuso. Use **/FR** en su lugar. Para obtener más información, consulte Opciones de compilador en desuso y quitadas en [Compiler Options Listed by Category](compiler-options-listed-by-category.md).

> [!NOTE]
> No cambie la extensión. sbr. BSCMAKE requiere esta extensión en los archivos intermedios.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. En el panel de navegación, elija **C o C++** y, a continuación, página de propiedades **Información de examen** .

1. Modifique el **Archivo de información de examen** o la propiedad **Habilitar información de examen** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformation%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BrowseInformationFile%2A>.

## <a name="see-also"></a>Consulte también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
