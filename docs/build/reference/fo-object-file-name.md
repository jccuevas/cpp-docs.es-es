---
title: /Fo (Nombre del archivo objeto)
ms.date: 11/04/2016
f1_keywords:
- /Fo
- VC.Project.VCCLCompilerTool.ObjectFile
- VC.Project.VCCLWCECompilerTool.ObjectFile
helpviewer_keywords:
- Fo compiler option [C++]
- object files, naming
- /Fo compiler option [C++]
- -Fo compiler option [C++]
ms.assetid: 0e6d593e-4e7f-4990-9e6e-92e1dcbcf6e6
ms.openlocfilehash: a8f2c1a196f18e6d310fd41d4dbed751440a4c20
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293048"
---
# <a name="fo-object-file-name"></a>/Fo (Nombre del archivo objeto)

Especifica un nombre de archivo objeto (.obj) o un directorio que se utilizará en lugar del predeterminado.

## <a name="syntax"></a>Sintaxis

```
/Fopathname
```

## <a name="remarks"></a>Comentarios

Si no usa esta opción, el archivo de objeto utiliza el nombre base del archivo de código fuente y la extensión de obj. Puede usar cualquier nombre y extensión que desee, pero la convención recomendada consiste en usar. obj.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Archivos de salida** .

1. Modificar el **nombre del archivo objeto** propiedad.  En el entorno de desarrollo, el archivo de objeto debe tener la extensión. obj.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos crea un archivo de objeto denominado THIS.obj en un directorio existente, \OBJECT, en la unidad B.

```
CL /FoB:\OBJECT\ THIS.C
```

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
