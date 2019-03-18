---
title: /X (Omitir rutas de acceso de inclusión estándar)
ms.date: 11/04/2016
f1_keywords:
- /x
- VC.Project.VCCLCompilerTool.OVERWRITEStandardIncludePath
- VC.Project.VCCLWCECompilerTool.OVERWRITEStandardIncludePath
helpviewer_keywords:
- /X compiler option [C++]
- include files, ignore standard path
- -X compiler option [C++]
- include directories, ignore standard
- X compiler option
- Ignore Standard Include Paths compiler option
ms.assetid: 16bdf2cc-c8dc-46e4-bdcc-f3caeba5e1ef
ms.openlocfilehash: dba7e49880307002a3dee983264e93666adfef17
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818406"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Omitir rutas de acceso de inclusión estándar)

Impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno PATH e INCLUDE.

## <a name="syntax"></a>Sintaxis

```
/X
```

## <a name="remarks"></a>Comentarios

Puede usar esta opción con la [/I (directorios de inclusión adicionales)](i-additional-include-directories.md) (**/I**`directory`) opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **preprocesador** página de propiedades.

1. Modificar el **Omitir ruta de acceso de incluir estándar** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.IgnoreStandardIncludePath%2A>.

## <a name="example"></a>Ejemplo

En el siguiente comando, `/X` indica al compilador que omita las ubicaciones especificadas por las variables de entorno PATH e INCLUDE y `/I` especifica el directorio en el que se va a buscar archivos de inclusión:

```
CL /X /I \ALT\INCLUDE MAIN.C
```

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
