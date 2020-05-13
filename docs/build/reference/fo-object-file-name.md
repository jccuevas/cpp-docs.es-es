---
title: /Fo (Nombre del archivo objeto)
description: Guía de referencia para la opción del compilador Microsoft C++ /Fo (nombre de archivo de objeto) en Visual Studio.
ms.date: 04/20/2020
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
ms.openlocfilehash: cd22ba745128fe1df67853d98c1495491b9ca840
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81748974"
---
# <a name="fo-object-file-name"></a>/Fo (Nombre del archivo objeto)

Especifica un nombre*`.obj`* de archivo o directorio de objetos que se utilizará en lugar del valor predeterminado.

## <a name="syntax"></a>Sintaxis

> **`/Fo`**_Ruta_

## <a name="remarks"></a>Observaciones

Puede utilizar **`/Fo`** la opción del compilador para establecer un directorio de salida para todos los archivos de objeto generados por el mandato del compilador CL. O bien, puede usarlo para cambiar el nombre de un archivo de objeto único.

De forma predeterminada, los archivos de objeto generados por el compilador se colocan en el directorio actual. Se les da el nombre base del *`.obj`* archivo de origen y una extensión.

Para utilizar **`/Fo`** la opción para cambiar el nombre de un archivo de objeto, especifique el nombre de archivo de salida como argumento *pathname.* Al cambiar el nombre de un archivo de objeto, puede usar cualquier *`.obj`* nombre y extensión que desee, pero la convención recomendada es usar . El compilador genera el error de línea de comandos D8036 si especifica un nombre de archivo cuando **`/Fo`** ha especificado más de un archivo de origen para compilar.

Para utilizar **`/Fo`** la opción para establecer un directorio de salida para todos los archivos de objeto creados por el mandato CL, especifique el directorio como argumento *pathname.* Un directorio se indica mediante una barra diagonal final en el argumento *pathname.* El directorio especificado debe existir; no se crea automáticamente.

## <a name="example"></a>Ejemplo

La siguiente línea de comandos crea un archivo de objeto denominado *sample.obj* en un directorio existente, * \\intermedio,* en la unidad D.

```cmd
CL /Fo"D:\intermediate\" /EHsc /c sample.cpp
```

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Establezca la opción en Visual Studio o mediante programación

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades** > de configuración**C/C++.** > **Output Files**

1. Modifique la propiedad **Nombre de archivo** de objeto para establecer el directorio de salida. En el IDE, el archivo de *`.obj`* objeto debe tener una extensión de .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ObjectFile%2A>.

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
