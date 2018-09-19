---
title: -Yc (crear archivo de encabezado precompilado) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- devlang-cpp
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.UsePrecompiledHeader
- /yc
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderThrough
- VC.Project.VCCLWCECompilerTool.UsePrecompiledHeader
- VC.Project.VCCLCompilerTool.PrecompiledHeaderThrough
dev_langs:
- C++
helpviewer_keywords:
- precompiled header files, creating
- PCH files, creating
- .pch files, creating
- -Yc compiler option [C++]
- /Yc compiler option [C++]
- Yc compiler option [C++]
ms.assetid: 47c2e555-b4f5-46e6-906e-ab5cf21f0678
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5288e748956a405073697ddd7331a73b95d8650
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45714251"
---
# <a name="yc-create-precompiled-header-file"></a>/Yc (Crear archivo de encabezado precompilado)

Indica al compilador que cree un archivo de encabezado precompilado (.pch) que representa el estado de la compilación en un momento determinado.

## <a name="syntax"></a>Sintaxis

> __/Yc__
>  __/Yc__*nombre de archivo*

## <a name="arguments"></a>Argumentos

*filename*<br/>
Especifica un archivo de encabezado (. h). Cuando se usa este argumento, el compilador compila todo el código hasta e incluyendo el archivo. h.

## <a name="remarks"></a>Comentarios

Cuando **/Yc** se especifica sin un argumento, el compilador compila todo el código hasta el final del archivo de base de código fuente o hasta el punto en el archivo de base donde un [hdrstop](../../preprocessor/hdrstop.md) se produce la directiva. El archivo .pch resultante tiene el mismo nombre base que el archivo de base de código fuente a menos que especifique un nombre de archivo diferente mediante la **hdrstop** pragma o **/FP** opción.

El código precompilado se guarda en un archivo con un nombre creado a partir del nombre base del archivo especificado con el **/Yc** opción y una extensión .pch. También puede usar el  [ /fp (nombre. Archivos PCH)](../../build/reference/fp-name-dot-pch-file.md) opción para especificar un nombre para el archivo de encabezado precompilado.

Si usas __/Yc__*filename*, el compilador compila todo el código hasta e incluyendo el archivo especificado para su uso posterior con el [/Yu (utilizar el archivo de encabezado precompilado)](../../build/reference/yu-use-precompiled-header-file.md) opción.

Si las opciones __/Yc__*filename* y __/Yu__*filename* se producen en la misma línea de comandos y ambas hacen referencia o implican el mismo nombre de archivo, __/Yc__*filename* tiene prioridad. Esta característica simplifica la escritura de archivos MAKE.

Para obtener más información sobre los encabezados precompilados, vea:

- [/Y (Encabezados precompilados)](../../build/reference/y-precompiled-headers.md)

- [Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Seleccione un archivo. cpp. El archivo .cpp debe #include el archivo .h que contiene información de encabezado precompilado. El proyecto **/Yc** puede invalidar la configuración en el nivel de archivo.

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Abra el **propiedades de configuración**, **C o C++**, **encabezados precompilados** página de propiedades.

1. Modificar el **encabezado precompilado** propiedad.

1. Para establecer el nombre de archivo, modifique el **el archivo de encabezado precompilado** propiedad.

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

Cuando este código se compila con el comando `CL /YcMYAPP.H PROG.CPP`, el compilador guarda todo el preprocesamiento de AFXWIN.h, RESOURCE.h y MYAPP.h en un archivo de encabezado precompilado denominado MYAPP.pch.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[Crear archivos de encabezado precompilados](../../build/reference/creating-precompiled-header-files.md)