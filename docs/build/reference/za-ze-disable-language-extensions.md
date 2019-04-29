---
title: /Za, /Ze (Deshabilitar extensiones de lenguaje)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 1db1dbdba4829ccf939cdc4f07ccfefe2474a35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315890"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Deshabilitar extensiones de lenguaje)

El **/Za** opción del compilador deshabilita y emite errores para las extensiones de Microsoft para C que no son compatibles con ANSI/ISO C89 C90. El desuso **/Ze** opción del compilador permite a las extensiones de Microsoft. Las extensiones de Microsoft están habilitadas de manera predeterminada.

## <a name="syntax"></a>Sintaxis

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>Comentarios

> [!NOTE]
> El uso de **/Za** cuando el código se compila como C++ no se recomienda. El **/Ze** opción es obsoleta porque su comportamiento está activada de forma predeterminada. Para obtener una lista de opciones del compilador en desuso, consulte [en desuso y opciones del compilador quitó](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

El compilador de Microsoft C/C ++ admite la compilación de código de C de dos maneras:

- El compilador usa el modo de compilación de C de forma predeterminada cuando un archivo de origen tiene un *.c* extensión, o cuando el [/TC](tc-tp-tc-tp-specify-source-file-type.md) o [/TC](tc-tp-tc-tp-specify-source-file-type.md) se especifica la opción. El compilador de C es un compilador C89/C90 que, de forma predeterminada, permite a las extensiones de Microsoft para el lenguaje c. Para obtener más información acerca de las extensiones específicas, consulte [Extensions Microsoft C y C++](microsoft-extensions-to-c-and-cpp.md). Cuando ambos compilación de C y la **/Za** opción se especifica, el compilador de C se ajusta estrictamente la norma C89/C90. El compilador trata las palabras clave como identificadores simples de extendidas de Microsoft, deshabilita las demás extensiones de Microsoft y define automáticamente el [ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md) predefinidos macro para programas de C.

- El compilador puede compilar el código de C en el modo de compilación de C++. Este comportamiento es el valor predeterminado para los archivos de origen que no tienen un *.c* extensión y cuándo el [/Tp](tc-tp-tc-tp-specify-source-file-type.md) o [/TP](tc-tp-tc-tp-specify-source-file-type.md) se especifica la opción. En el modo de compilación de C++, el compilador admite las partes de los estándares ISO C99 y C11 que se han incorporado en el estándar de C++. Casi todo el código de C también es código de C++ válido. Un pequeño número de palabras clave de C y construcciones de código no es de código de C++ válido o se interpreta de forma distinta en C++. El compilador se comporta según el estándar en estos casos de C++. En el modo de compilación de C++, el **/Za** opción puede provocar un comportamiento inesperado y no se recomienda.

Otras opciones del compilador pueden afectar a cómo el compilador garantiza el cumplimiento de estándares. Para que las formas de especificar el estándar C y C++ comportamiento configuración específica, consulte el [/Zc](zc-conformance.md) opción del compilador. Para ver otras opciones de cumplimiento estándar de C++, vea el [/ permissive-](permissive-standards-conformance.md) y [/std](std-specify-language-standard-version.md) opciones del compilador.

Para obtener más información acerca de problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. En el panel de navegación, elija **propiedades de configuración** > **C o C++** > **lenguaje**.

1. Modificar el **deshabilitar extensiones de lenguaje** propiedad.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](compiler-options.md)<br/>
[/Zc (Ajuste)](zc-conformance.md)<br/>
[/permissive/ (Conformidad de los estándares)](permissive-standards-conformance.md)<br/>
[/std (Especificar la versión estándar del lenguaje)](std-specify-language-standard-version.md)<br/>
