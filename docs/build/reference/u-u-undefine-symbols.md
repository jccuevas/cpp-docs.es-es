---
title: /U, /u (Anular la definición de símbolos)
ms.date: 06/08/2020
f1_keywords:
- VC.Project.VCCLCompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLWCECompilerTool.UndefinePreprocessorDefinitions
- VC.Project.VCCLCompilerTool.UndefineAllPreprocessorDefinitions
- /u
- VC.Project.VCCLWCECompilerTool.UndefineAllPreprocessorDefinitions
helpviewer_keywords:
- -U compiler option [C++]
- Undefine Symbols compiler option
- /U compiler option [C++]
- U compiler option [C++]
ms.assetid: 7bc0474f-6d1f-419b-807d-0d8816763b2a
ms.openlocfilehash: 4d7a2b3d5df2b22dc53eb7b58bfb78cdb1824b26
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616660"
---
# <a name="u-u-undefine-symbols"></a>/U, /u (Anular la definición de símbolos)

La **`/U`** opción del compilador anula la definición del símbolo de preprocesador especificado. La **`/u`** opción del compilador anula la definición de los símbolos específicos de Microsoft que define el compilador.

## <a name="syntax"></a>Sintaxis

> **`/U`**\[]*Symbol*\
> **`/u`**

## <a name="arguments"></a>Argumentos

*símbolo*<br/>
Símbolo de preprocesador que se va a anular.

## <a name="remarks"></a>Observaciones

Ninguna de las **`/U`** **`/u`** Opciones y puede anular la definición de un símbolo creado mediante la **`#define`** Directiva.

La **`/U`** opción puede anular la definición de un símbolo que se definió anteriormente mediante la **`/D`** opción.

De forma predeterminada, el compilador puede definir un gran número de símbolos específicos de Microsoft. Estos son algunos comunes:

| Símbolo | Función |
|--|--|
| `_CHAR_UNSIGNED` | El tipo de carácter predeterminado es sin signo. Definido cuando [**`/J`**](j-default-char-type-is-unsigned.md) se especifica la opción. |
| `_CPPRTTI` | Definido para el código compilado con la [**`/GR`**](gr-enable-run-time-type-information.md) opción. |
| `_CPPUNWIND` | Definido para el código compilado con la [**`/EHsc`**](eh-exception-handling-model.md) opción. |
| `_DLL` | Definido cuando [**`/MD`**](md-mt-ld-use-run-time-library.md) se especifica la opción. |
| `_M_IX86` | De forma predeterminada, se define como 600 para los destinos de x86. |
| `_MSC_VER` | Se define como un valor entero único para cada versión del compilador. Para obtener más información, vea [macros predefinidas](../../preprocessor/predefined-macros.md). |
| `_WIN32` | Definido para aplicaciones WIN32. Siempre definido. |
| `_MT` | Definido cuando se especifica la opción [ **`/MD`** o **`/MT`** ](md-mt-ld-use-run-time-library.md) . |

Para obtener una lista completa de las macros predefinidas específicas de Microsoft, vea [macros predefinidas](../../preprocessor/predefined-macros.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades opciones de **configuración**  >  avanzadas de**C/C++**  >  **Advanced** .

1. Modifique las propiedades de **anular definiciones del preprocesador** o **anular la definición de todas las definiciones del preprocesador** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefineAllPreprocessorDefinitions%2A> o <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UndefinePreprocessorDefinitions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[**`/J`**(El tipo de carácter predeterminado es sin signo)](j-default-char-type-is-unsigned.md)<br/>
[**`/GR`**(Habilitar información de tipo en tiempo de ejecución)](gr-enable-run-time-type-information.md)<br/>
[**`/EH`**(Modelo de control de excepciones)](eh-exception-handling-model.md)<br/>
[**`/MD`**, **`/MT`** , **`/LD`** (Usar la biblioteca en tiempo de ejecución)](md-mt-ld-use-run-time-library.md)
