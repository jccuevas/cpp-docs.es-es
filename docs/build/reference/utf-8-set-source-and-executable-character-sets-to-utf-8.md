---
title: /UTF-8 (establecer los juegos de caracteres de origen y UTF-8de ejecución en)
ms.date: 04/26/2020
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
no-loc:
- UTF
- UTF-8
- UTF-16
ms.openlocfilehash: c98a30b0ec4b36b8bd87fb0956d9382751975cfd
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168870"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-opno-locutf-8"></a>`/utf-8`(Establecer los juegos de caracteres de origen y UTF-8de ejecución en)

Especifica el juego de caracteres de origen y el juego de caracteres UTF-8de ejecución como.

## <a name="syntax"></a>Sintaxis

> **`/utf-8`**

## <a name="remarks"></a>Observaciones

Puede utilizar la **`/utf-8`** opción para especificar los juegos de caracteres de origen y de ejecución como codificados mediante UTF-8. Es equivalente a especificar **`/source-charset:utf-8 /execution-charset:utf-8`** en la línea de comandos. Cualquiera de estas opciones también habilita la **`/validate-charset`** opción de forma predeterminada. Para obtener una lista de identificadores de páginas de códigos y nombres de juegos de caracteres compatibles, vea [identificadores de páginas de códigos](/windows/win32/Intl/code-page-identifiers).

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de código fuente se encuentra en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de código fuente se codifica mediante la página de códigos del usuario actual, a menos que **`/utf-8`** haya especificado **`/source-charset`** una página de códigos mediante o la opción. Visual Studio permite guardar el código fuente de C++ mediante el uso de varias codificaciones de caracteres. Para obtener información sobre los juegos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.

## <a name="set-the-option-in-visual-studio-or-programmatically"></a>Establecer la opción en Visual Studio o mediante programación

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades**línea de comandos** de**C/C++** > de **propiedades** > de configuración.

1. En **opciones adicionales**, agregue la **`/utf-8`** opción para especificar la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (establecer juego de caracteres de ejecución)](execution-charset-set-execution-character-set.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](source-charset-set-source-character-set.md)<br/>
[/validate/charset (Validar los caracteres compatibles)](validate-charset-validate-for-compatible-characters.md)
