---
title: /Tc, /Tp, /TC, /TP (Especificar el tipo de archivo de código fuente)
ms.date: 01/11/2018
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
ms.openlocfilehash: fa35249983284261252c8ada65e79ed1cb6ec79a
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825397"
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Especificar el tipo de archivo de código fuente)

La opción **/TC** especifica que el argumento FILENAME es un archivo de código fuente de C, incluso si no tiene una extensión. C. La opción **/TP** especifica que el argumento FILENAME es un archivo de código fuente de C++, incluso si no tiene una extensión. cpp o. CXX. Un espacio entre la opción y el nombre de archivo es opcional. Cada opción especifica un archivo; para especificar archivos adicionales, repita la opción.

**/TC** y **/TP** son variantes globales de **/TC** y **/TP**. Especifican al compilador que trate todos los archivos denominados en la línea de comandos como archivos de código fuente de C (**/TC**) o archivos de código fuente de C++ (**/TP**), sin tener en cuenta la ubicación en la línea de comandos con respecto a la opción. Estas opciones globales se pueden invalidar en un solo archivo por medio de **/TC** o **/TP**.

## <a name="syntax"></a>Sintaxis

> **/TC** _nombreDeArchivo_\
> **/Tp** _Nombre de archivo_ /TP\
> **/TC**\
> **/TP**

### <a name="arguments"></a>Argumentos

*extensión*<br/>
Un archivo de código fuente de C o C++.

## <a name="remarks"></a>Observaciones

De forma predeterminada, **cl** supone que los archivos con la extensión. c son archivos de código fuente de c y archivos con la extensión. cpp o. CXX son archivos de código fuente de C++.

Cuando se especifica la opción **TC** o **TC** , se omite cualquier especificación de la opción [/Zc: Wchar_t (wchar_t es de tipo nativo)](zc-wchar-t-wchar-t-is-native-type.md) .

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**Opciones** de **configuración** > avanzadas de**C/C++** > .

1. Modifique la propiedad **compilar como** . Elija **Aceptar** o **aplicar** para aplicar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Ejemplos

Esta línea de comandos de CL especifica que MAIN. c, TEST. PRG y COLLAte. PRG son todos los archivos de código fuente de C. CL no reconocerá PRINT. PRG.

> CL MAIN. C/TcTEST.PRG/TcCOLLATE.PRG PRINT. PRG

Esta línea de comandos de CL especifica que TEST1. c, TEST2. CXX, TEST3. EH y TEST4. o se compilan como archivos de C++ y TEST5. z se compila como un archivo de C.

> CL TEST1. C TEST2. CXX TEST3. EH TEST4. O/TC TEST5. Z/TP

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
