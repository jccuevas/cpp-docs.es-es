---
title: /FP (nombre &period;archivo PCH)
description: Use la opción del compilador/FP para especificar el nombre del archivo de encabezado precompilado.
ms.date: 05/31/2019
f1_keywords:
- VC.Project.VCCLCompilerTool.PrecompiledHeaderFile
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
ms.openlocfilehash: d62c5bd9fc7920c0a2a5530879680fad2a01d39a
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79439782"
---
# <a name="fp-name-periodpch-file"></a>/FP (nombre &period;archivo PCH)

Proporciona un nombre de ruta de acceso para un encabezado precompilado en lugar de utilizar el nombre de ruta de acceso predeterminado.

## <a name="syntax"></a>Sintaxis

> **/FP**(<em>nombreruta</em> )

## <a name="remarks"></a>Observaciones

Use la opción **/FP** con [/YC (crear archivo de encabezado precompilado)](yc-create-precompiled-header-file.md) o [/Yu (usar archivo de encabezado precompilado)](yu-use-precompiled-header-file.md) para especificar la ruta de acceso y el nombre de archivo para el archivo de encabezado precompilado (PCH). De forma predeterminada, la opción **/YC** crea un nombre de archivo PCH mediante el nombre base del archivo de código fuente y una extensión *PCH* .

Si no especifica una extensión como parte del *nombreruta*, se supone que se trata de una extensión de *PCH* . Cuando se especifica un nombre de directorio mediante el uso de una barra diagonal ( **/** ) al final del nombre de *ruta*de acceso, el nombre de archivo predeterminado es VC*version*0. PCH, donde *version* es la versión principal del conjunto de herramientas de Visual Studio. Este directorio debe existir o se genera el error C1083.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra las **propiedades de configuración** > página de propiedades **encabezados precompilados** de **C/C++**  > .

1. Modifique la propiedad **archivo de salida del encabezado precompilado** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Ejemplos

Para crear una versión con nombre independiente del archivo de encabezado precompilado para la compilación de depuración del programa, puede especificar un comando como:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

El siguiente comando especifica el uso de un archivo de encabezado precompilado denominado MYPCH. pch. El compilador precompila el código fuente en PROG. cpp hasta el final de MYAPP. h y coloca el código precompilado en MYPCH. pch. A continuación, usa el contenido de MYPCH. pch y compila el resto de PROG. cpp para crear un archivo. obj. La salida de este ejemplo es un archivo denominado PROG. exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Consulte también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
