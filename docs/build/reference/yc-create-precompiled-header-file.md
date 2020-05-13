---
title: /Yc (Crear archivo de encabezado precompilado)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
ms.openlocfilehash: 71a05df3adc74edfd814bb6dc15121e4a343dc4d
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825761"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Crear archivo de encabezado precompilado)

Indica al compilador que cree un archivo de encabezado precompilado (. pch) que represente el estado de compilación en un punto determinado.

## <a name="syntax"></a>Sintaxis

> __/YC__\
> __/YC__*nombrearchivo*

## <a name="arguments"></a>Argumentos

*extensión*<br/>
Especifica un archivo de encabezado (. h). Cuando se usa este argumento, el compilador compila todo el código hasta el archivo. h incluido.

## <a name="remarks"></a>Observaciones

Cuando se especifica **/YC** sin un argumento, el compilador compila todo el código hasta el final del archivo de origen base o hasta el punto del archivo base donde se produce una directiva [hdrstop](../../preprocessor/hdrstop.md) . El archivo. pch resultante tiene el mismo nombre base que el archivo de origen base, a menos que especifique un nombre de archivo diferente mediante la pragma **hdrstop** o la opción **/FP** .

El código precompilado se guarda en un archivo con un nombre creado a partir del nombre base del archivo especificado con la opción **/YC** y una extensión. pch. También puede usar [/FP (nombre. Archivo PCH)](fp-name-dot-pch-file.md) para especificar un nombre para el archivo de encabezado precompilado.

Si usa __/YC__*filename*, el compilador compila todo el código hasta el archivo especificado y lo incluye para su uso posterior con la opción [/Yu (usar el archivo de encabezado precompilado)](yu-use-precompiled-header-file.md) .

Si las opciones __/YC__*filename* y __/Yu__*filename* aparecen en la misma línea de comandos y hacen referencia, o implican, el mismo nombre de archivo, __/YC__*filename* tiene prioridad. Esta característica simplifica la escritura de archivos make.

Para obtener más información sobre los encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](y-precompiled-headers.md)

- [Archivos de encabezado precompilados](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Seleccione un archivo. cpp. El archivo. cpp debe #include el archivo. h que contiene la información de encabezado precompilado. La configuración de **/YC** del proyecto se puede invalidar en el nivel de archivo.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra la página de **propiedades propiedades de configuración**, **C/C++**, **encabezados precompilados** .

1. Modifique la propiedad del **encabezado precompilado** .

1. Para establecer el nombre de archivo, modifique la propiedad **archivo de encabezado precompilado** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Ejemplo

Observe el código siguiente:

```cpp
// prog.cpp
// compile with: cl /c /Ycmyapp.h prog.cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
// ...
```

Cuando este código se compila con el comando `CL /YcMYAPP.H PROG.CPP`, el compilador guarda todo el preprocesamiento de AFXWIN. h, Resource. h y MyApp. h en un archivo de encabezado precompilado denominado myapp. pch.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Archivos de encabezado precompilados](../creating-precompiled-header-files.md)
