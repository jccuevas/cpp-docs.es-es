---
title: / Validate/CharSet (validar los caracteres compatibles)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 30c818bcb64c2f2ee57c05a4870e7d30afe98cfe
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810073"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/ Validate/CharSet (validar los caracteres compatibles)

Valida que el texto del archivo de origen contiene únicamente caracteres que se puede representar como UTF-8.

## <a name="syntax"></a>Sintaxis

```
/validate-charset[-]
```

## <a name="remarks"></a>Comentarios

Puede usar el **/Validate/CharSet** opción para validar que el código fuente contiene solo el conjunto de caracteres que se pueden representar en ambos el carácter de origen y el juego de caracteres de la ejecución. Esta comprobación se habilita automáticamente cuando se especifica **/Source-CharSet**, **/Execution-CharSet**, o **/UTF-8** opciones del compilador. Puede deshabilitar explícitamente esta comprobación especificando el **/ validate-charset -** opción.

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que haya especificado una página de códigos mediante **/UTF-8** o **/Source-CharSet** opción. Visual Studio le permite guardar el código fuente de C++ mediante cualquiera de las varias codificaciones de caracteres. Para obtener información acerca de los juegos de caracteres de origen y ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje. Para obtener una lista de admite identificadores de páginas de código y juego de caracteres de nombres, vea [identificadores de páginas de código](/windows/desktop/Intl/code-page-identifiers).

Visual Studio usa UTF-8 como la codificación de caracteres interno durante la conversión entre el juego de caracteres de origen y el juego de caracteres de ejecución. Si no se puede representar un carácter en el archivo de origen en el juego de caracteres de ejecución, la conversión de UTF-8 se sustituye por un signo de interrogación '?' caracteres. El **/Validate/CharSet** opción hace que la compilación notificar una advertencia si esto ocurre.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda el **propiedades de configuración**, **C o C++**, **línea de comandos** carpeta.

1. En **opciones adicionales**, agregue el **/Validate/CharSet** opción y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/ Execution-CharSet (establecer juego de caracteres de ejecución)](execution-charset-set-execution-character-set.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
