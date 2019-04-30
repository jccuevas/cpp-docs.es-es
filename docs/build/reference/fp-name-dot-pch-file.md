---
title: /Fp (Dar nombre al archivo .Pch)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
- /fp
- VC.Project.VCCLWCECompilerTool.PrecompiledHeaderFile
helpviewer_keywords:
- Fp compiler option [C++]
- -Fp compiler option [C++]
- naming precompiler header files
- PCH files, naming
- names [C++], PCH
- .pch files, naming
- precompiled header files, naming
- /Fp compiler option [C++]
ms.assetid: 0fcd9cbd-e09f-44d3-9715-b41efb5d0be2
ms.openlocfilehash: 95506e17dff47e51cb7a3d83b629880f63422d26
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270997"
---
# <a name="fp-name-pch-file"></a>/Fp (Dar nombre al archivo .Pch)

Proporciona un nombre de ruta de acceso para un encabezado precompilado en lugar de usar el nombre de ruta de acceso predeterminada.

## <a name="syntax"></a>Sintaxis

> **/ FP**<em>pathname</em>

## <a name="remarks"></a>Comentarios

Use esta opción con [/Yc (crear archivo de encabezado precompilado)](yc-create-precompiled-header-file.md) o [/Yu (utilizar el archivo de encabezado precompilado)](yu-use-precompiled-header-file.md) para proporcionar un nombre de ruta de acceso para un encabezado precompilado en lugar de usar el nombre de ruta de acceso predeterminada. También puede usar **/FP** con **/Yc** para especificar el uso de un archivo de encabezado precompilado que difiere de la **/Yc**<em>filename</em> argumento y desde el nombre base del archivo de origen.

Si no especifica una extensión como parte del nombre de ruta de acceso, se supone una extensión pch. Si especifica un directorio sin un nombre de archivo, el nombre de archivo predeterminado es VC*x*0.pch, donde *x* es la versión principal de Visual C++ en uso.

También puede usar el **/FP** opción con **/Yu**.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en el **encabezados precompilados** página de propiedades.

1. Modificar el **el archivo de encabezado precompilado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderFile%2A>.

## <a name="example"></a>Ejemplo

Si desea crear un archivo de encabezado precompilado para una versión de depuración del programa y compila los archivos de encabezado y código fuente, puede especificar un comando como:

```
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

## <a name="example"></a>Ejemplo

El siguiente comando Especifica el uso de un archivo de encabezado precompilado denominado MYPCH.pch. El compilador supone que el código fuente de PROG.cpp se ha precompilado mediante MYAPP.h y que el código precompilado reside en MYPCH.pch. Usa el contenido de MYPCH.pch y compila el resto de PROG.cpp para crear un archivo .obj. La salida de este ejemplo es un archivo denominado PROG.exe.

```
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
