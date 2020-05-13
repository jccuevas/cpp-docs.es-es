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
ms.openlocfilehash: 9a2584591f6ca22d6767a5c447ffb72bea0a78ea
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825880"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Deshabilitar extensiones de lenguaje)

La opción del compilador **/za** deshabilita y emite errores para las extensiones de Microsoft a C que no son compatibles con ANSI C89/ISO C90. La opción de compilador **/ze** desusada habilita las extensiones de Microsoft. Las extensiones de Microsoft están habilitadas de manera predeterminada.

## <a name="syntax"></a>Sintaxis

> **/Za**\
> **/Ze**

## <a name="remarks"></a>Observaciones

> [!NOTE]
> El uso de **/za** cuando el código se compila como C++ no se recomienda. La opción **/ze** está en desuso porque su comportamiento está activado de forma predeterminada. Para obtener una lista de opciones del compilador en desuso, vea [Opciones del compilador en desuso y quitadas](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

El compilador de C/C++ de Microsoft admite la compilación de código de C de dos maneras:

- El compilador utiliza el modo de compilación de C de forma predeterminada cuando un archivo de código fuente tiene una extensión *. C* o cuando se especifica la opción [/TC](tc-tp-tc-tp-specify-source-file-type.md) o [/TC](tc-tp-tc-tp-specify-source-file-type.md) . El compilador de C es un compilador de C89/C90 que habilita de forma predeterminada las extensiones de Microsoft para el lenguaje C. Para obtener más información acerca de las extensiones específicas, vea [extensiones de Microsoft para C y C++](microsoft-extensions-to-c-and-cpp.md). Cuando se especifican la compilación de C y la opción **/za** , el compilador de c se ajusta estrictamente al estándar C89/C90. El compilador trata las palabras clave extendidas de Microsoft como identificadores simples, deshabilita las otras extensiones de Microsoft y define automáticamente la macro predefinida [ \_ \_stdc\_ ](../../preprocessor/predefined-macros.md) para los programas de C.

- El compilador puede compilar código C en el modo de compilación de C++. Este comportamiento es el predeterminado para los archivos de código fuente que no tienen la extensión *. c* y cuando se especifica la opción [/TP](tc-tp-tc-tp-specify-source-file-type.md) o [/TP](tc-tp-tc-tp-specify-source-file-type.md) . En el modo de compilación de C++, el compilador admite esas partes de los estándares ISO C99 y C11 que se han incorporado en el estándar de C++. Casi todo el código C también es código de C++ válido. Un pequeño número de construcciones de código y palabras clave de C no es un código de C++ válido o se interpreta de manera diferente en C++. En estos casos, el compilador se comporta de acuerdo con el estándar de C++. En el modo de compilación de C++, la opción **/za** puede producir un comportamiento inesperado y no se recomienda.

Otras opciones del compilador pueden afectar a la forma en que el compilador garantiza la conformidad con los estándares. Para obtener información sobre cómo especificar la configuración de comportamiento estándar de C y C++, consulte la opción del compilador [/ZC](zc-conformance.md) . Para obtener más opciones de configuración de cumplimiento estándar de C++, vea las opciones del compilador [/permissive-](permissive-standards-conformance.md) y [/STD](std-specify-language-standard-version.md) .

Para obtener más información sobre los problemas de conformidad con Visual C++, vea [comportamiento no estándar](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener detalles, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. En el panel de navegación, elija **propiedades** > de configuración**lenguaje****C/C++** > .

1. Modifique la propiedad **deshabilitar extensiones de lenguaje** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador](compiler-options.md)<br/>
[/Zc (Ajuste)](zc-conformance.md)<br/>
[/permissive/ (Conformidad de los estándares)](permissive-standards-conformance.md)<br/>
[/STD (especificar la versión estándar del lenguaje)](std-specify-language-standard-version.md)<br/>
