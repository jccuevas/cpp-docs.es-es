---
title: / Tc, /Tp, / TC, /TP (especificar el tipo de archivo de origen) | Documentos de Microsoft
ms.date: 1/11/2018
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.CompileAs
- VC.Project.VCCLCompilerTool.CompileAs
- /Tp
- /tc
dev_langs: C++
helpviewer_keywords:
- Tp compiler option [C++]
- /Tc compiler option [C++]
- -Tc compiler option [C++]
- source files, specifying to compiler
- Tc compiler option [C++]
- /Tp compiler option [C++]
- -Tp compiler option [C++]
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3d51e4c6bbf6a77f86be5cabde9b65f8e4f8c9f
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
---
# <a name="tc-tp-tc-tp-specify-source-file-type"></a>/Tc, /Tp, /TC, /TP (Especificar el tipo de archivo de código fuente)

El **/TC** opción especifica que el argumento de nombre de archivo es un archivo de código fuente de C, incluso si no tiene una extensión. c. El **/Tp** opción especifica que el argumento de nombre de archivo es un archivo de código fuente de C++, incluso si no tiene una extensión .cpp o .cxx. Un espacio entre la opción y el nombre de archivo es opcional. Cada opción especifica un archivo; para especificar archivos adicionales, repita la opción.

**/ TC** y **/TP** son variantes globales de **/TC** y **/Tp**. Especifica que el compilador trate todos los archivos con el nombre en la línea de comandos como archivos de código fuente de C (**/TC**) o archivos de código fuente de C++ (**/TP**), independientemente de su ubicación en la línea de comandos con respecto a la opción. Estas opciones globales se pueden invalidar en un único archivo por medio de **/TC** o **/Tp**.

## <a name="syntax"></a>Sintaxis

> **/Tc** _filename_  
> **/TP** _nombre de archivo_  
> **/TC**  
> **/TP**  

## <a name="arguments"></a>Argumentos

*filename*  
Un archivo de código fuente de C o C++.

## <a name="remarks"></a>Comentarios

De forma predeterminada, **CL** se da por supuesto que los archivos con la extensión .c son archivos de código fuente de C y archivos con el .cpp o la extensión .cxx son archivos de código fuente de C++.

Cuando ambos el **TC** o **Tc** se especifica la opción, cualquier especificación de la [/Zc: wchar_t (wchar_t es tipo nativo)](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md) se omite.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **avanzadas** página de propiedades.

1. Modificar el **compilar como** propiedad. Elija **Aceptar** o **aplicar** para aplicar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.CompileAs%2A>.

## <a name="examples"></a>Ejemplos

Esta línea de comandos de CL especifica que MAIN.c, TEST.prg y COLLATE.prg son todos los archivos de código fuente de C. CL no reconocerá a PRINT.prg.

> CL PRINCIPAL. C /TcTEST.PRG /TcCOLLATE.PRG imprimir. PRG

Esta línea de comandos de CL especifica que TEST1.c, TEST2.cxx, TEST3.huh y TEST4.o se compilan como archivos de C++, y TEST5.z se compila como un archivo de C.

> CL TEST1. C TEST2. CXX TEST3. ¿VERDAD TEST4. O/TC TEST5. /TP Z

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)  
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)  
