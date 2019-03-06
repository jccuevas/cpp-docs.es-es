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
ms.openlocfilehash: 615a53a7ad29527187072c3131f551a76bd18969
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57421387"
---
# <a name="x-ignore-standard-include-paths"></a>/X (Omitir rutas de acceso de inclusión estándar)

Impide que el compilador busque archivos de inclusión en los directorios especificados en las variables de entorno PATH e INCLUDE.

## <a name="syntax"></a>Sintaxis

```
/X
```

## <a name="remarks"></a>Comentarios

Puede usar esta opción con la [/I (directorios de inclusión adicionales)](../../build/reference/i-additional-include-directories.md) (**/I**`directory`) opción.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

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

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
