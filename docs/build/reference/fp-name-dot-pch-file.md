---
title: /Fp (nombre &period;archivo pch)
description: Utilice la opción del compilador/FP para especificar el nombre de archivo de encabezado precompilado.
ms.date: 05/31/2019
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
ms.openlocfilehash: 6e7faa934d14acb5d129173c5e0c7ee67d6caf2b
ms.sourcegitcommit: 540fa2f5015de1adfa7b6bf823f6eb4ed5a6a4bd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/03/2019
ms.locfileid: "66460880"
---
# <a name="fp-name-periodpch-file"></a>/Fp (nombre &period;archivo pch)

Proporciona un nombre de ruta de acceso para un encabezado precompilado en lugar de usar el nombre de ruta de acceso predeterminada.

## <a name="syntax"></a>Sintaxis

> **/ FP**<em>pathname</em>

## <a name="remarks"></a>Comentarios

Use la **/FP** opción con [/Yc (crear archivo de encabezado precompilado)](yc-create-precompiled-header-file.md) o [/Yu (utilizar el archivo de encabezado precompilado)](yu-use-precompiled-header-file.md) para especificar la ruta de acceso y nombre de archivo para el encabezado precompilado (PCH) archivo. De forma predeterminada, el **/Yc** opción crea un nombre de archivo PCH utilizando el nombre base del archivo de origen y un *pch* extensión.

Si no se especifica una extensión como parte de la *pathname*, una extensión de *pch* se da por hecho. Cuando se especifica un nombre de directorio mediante el uso de una barra diagonal ( **/** ) al final de *pathname*, el nombre de archivo predeterminado es vc*versión*0.pch, donde  *versión* es la versión principal del conjunto de herramientas de Visual Studio. Este directorio debe existir, o se genera el error C1083.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Abra el **propiedades de configuración** > **C /C++**  > **encabezados precompilados** página de propiedades.

1. Modificar el **archivo de salida del encabezado precompilado** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="examples"></a>Ejemplos

Para crear un versión del archivo de encabezado precompilado para la compilación de depuración del programa independiente, puede especificar un comando como:

```CMD
CL /DDEBUG /Zi /Yc /FpDPROG.PCH PROG.CPP
```

El siguiente comando Especifica el uso de un archivo de encabezado precompilado denominado MYPCH.pch. El compilador precompila el código fuente de PROG.cpp hasta el final del MYAPP.h y coloca el código precompilado en MYPCH.pch. A continuación, usa el contenido de MYPCH.pch y compila el resto de PROG.cpp para crear un archivo .obj. La salida de este ejemplo es un archivo denominado PROG.exe.

```CMD
CL /YuMYAPP.H /FpMYPCH.PCH PROG.CPP
```

## <a name="see-also"></a>Vea también

[/F (Opciones del archivo de resultados)](output-file-f-options.md)<br/>
[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[Especificar la ruta de acceso](specifying-the-pathname.md)
