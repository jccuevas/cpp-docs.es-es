---
title: /X (Omitir rutas de acceso de inclusión estándar)
ms.date: 07/18/2019
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLCompilerTool.IgnoreStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: 16f903b98d69472fe1a33b084fe6393ecf9ec001
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341044"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Omitir rutas de acceso de inclusión estándar)

Impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno PATH e INCLUDE.

## <a name="syntax"></a>Sintaxis

```
/X
```

## <a name="remarks"></a>Comentarios

Puede usar esta opción con la opción [/i (directorios de inclusión adicionales)](i-additional-include-directories.md) ( **/i**`directory`).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic  en la página de propiedades del preprocesador.

1. Modifique la propiedad **omitir ruta de acceso de inclusión estándar** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Ejemplo

En el siguiente comando, `/X` indica al compilador que omita las ubicaciones especificadas por las variables de entorno `/I` path e include, y especifica el directorio en el que buscar archivos de inclusión:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
