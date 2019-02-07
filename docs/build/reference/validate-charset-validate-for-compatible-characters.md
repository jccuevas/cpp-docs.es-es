---
title: / Validate/CharSet (validar los caracteres compatibles)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 69b43b603ef4711e1acc0bd612e0e1c949722dc9
ms.sourcegitcommit: bd637e9c39650cfd530520ea978a22fa4caa0e42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/07/2019
ms.locfileid: "55850083"
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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración**, **C o C++**, **línea de comandos** carpeta.

1. En **opciones adicionales**, agregue el **/Validate/CharSet** opción y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/ Execution-CharSet (establecer juego de caracteres de ejecución)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)