---
title: / MD, -MT, -LD (utilizar la biblioteca de tiempo de ejecución)
ms.date: 11/04/2016
f1_keywords:
- /ld
- /mt
- VC.Project.VCCLWCECompilerTool.RuntimeLibrary
- VC.Project.VCCLCompilerTool.RuntimeLibrary
- /md
- /ml
helpviewer_keywords:
- /MT compiler option [C++]
- -MD compiler option [C++]
- threading [C++], multithread compiler option
- MSVCRTD.lib
- MSVCRT.lib
- LIBCMT.lib
- MD compiler option [C++]
- /MD compiler option [C++]
- MT compiler option [C++]
- LD compiler option [C++]
- MDd compiler option [C++]
- -MDd compiler option [C++]
- LIBCD.lib
- -MTd compiler option [C++]
- MTd compiler option [C++]
- /MTd compiler option [C++]
- -LD compiler option [C++]
- /MDd compiler option [C++]
- multithread compiler option
- _STATIC_CPPLIB symbol
- LIBC.lib
- /LD compiler option [C++]
- DLLs [C++], compiler options
- LIBCMTD.lib
- -MT compiler option [C++]
ms.assetid: cf7ed652-dc3a-49b3-aab9-ad60e5395579
ms.openlocfilehash: 59b0483d76a2a98c1f278a323a827b243d21adea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321298"
---
# <a name="md-mt-ld-use-run-time-library"></a>/MD, /MT, /LD (utilizar la biblioteca en tiempo de ejecución)

Indica si un módulo multiproceso es un archivo DLL y especifica versiones comerciales o de depuración de la biblioteca en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```
/MD[d]
/MT[d]
/LD[d]
```

## <a name="remarks"></a>Comentarios

|Opción|Descripción|
|------------|-----------------|
|**/MD**|Hace que la aplicación use la versión específica para multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución. Define `_MT` y `_DLL` y hace que el compilador sitúe el nombre de la biblioteca MSVCRT.lib en el archivo .obj.<br /><br /> Las aplicaciones compiladas con esta opción se vinculan estáticamente con MSVCRT.lib. Esta biblioteca proporciona un nivel de código que permite al vinculador resolver referencias externas. El código de trabajo real se encuentra en el archivo MSVCR*versionnumber*. Archivo DLL, que debe estar disponible en tiempo de ejecución para las aplicaciones vinculadas con MSVCRT.lib.|
|**/MDd**|Define `_DEBUG`, `_MT` y `_DLL` y hace que la aplicación use la versión de depuración multiproceso y la versión específica para DLL de la biblioteca en tiempo de ejecución. También hace que el compilador coloque el nombre de la biblioteca MSVCRTD.lib en el archivo .obj.|
|**/MT**|Hace que la aplicación use la versión estática multiproceso de la biblioteca en tiempo de ejecución. Define `_MT` y hace que el compilador sitúe el nombre de biblioteca LIBCMT.lib en el archivo .obj para que el vinculador utilice LIBCMT.lib al resolver símbolos externos.|
|**/MTd**|Define `_DEBUG` y `_MT`. Esta opción también hace que el compilador coloque el nombre de la biblioteca LIBCMTD.lib en el archivo .obj, así el vinculador usará LIBCMTD.lib para resolver los símbolos externos.|
|**/LD**|Crea un archivo DLL.<br /><br /> Pasa el **/DLL** opción al vinculador. El vinculador busca una función `DllMain`, aunque esta función no es obligatoria. Si no escribe una función `DllMain`, el vinculador inserta una función `DllMain` que devuelve TRUE.<br /><br /> Vincula el código de inicio de DLL.<br /><br /> Crea una biblioteca de importación (.lib) si no se especifica un archivo de exportación (.exp) en la línea de comandos. Vincula la biblioteca de importación con aplicaciones que llaman al archivo DLL.<br /><br /> Interpreta [/Fe (nombre del archivo EXE)](fe-name-exe-file.md) como un archivo DLL en lugar de un archivo .exe de nomenclatura. De forma predeterminada, se convierte en el nombre del programa *basename*.dll en lugar de *basename*.exe.<br /><br /> Implica **/MT** a menos que especifique explícitamente **/MD**.|
|**/LDd**|Crea un archivo DLL de depuración. Define `_MT` y `_DEBUG`.|

Para obtener más información sobre las bibliotecas en tiempo de ejecución de C y las bibliotecas que se usan cuando se compila con [/CLR (Common Language Runtime Compilation)](clr-common-language-runtime-compilation.md), consulte [características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).

Todos los módulos pasados a una invocación específica del vinculador deben haberse compilados con la misma opción del compilador de la biblioteca en tiempo de ejecución (**/MD**, **/MT**, **/LD**).

Para obtener más información sobre cómo usar las versiones de depuración de las bibliotecas en tiempo de ejecución, consulte [C Run-Time Library Reference](../../c-runtime-library/c-run-time-library-reference.md).

Para obtener más información sobre los archivos DLL, consulte [archivos DLL en Visual C++](../dlls-in-visual-cpp.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el **C o C++** carpeta.

1. Seleccione el **generación de código** página de propiedades.

1. Modificar el **biblioteca en tiempo de ejecución** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.RuntimeLibrary%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
