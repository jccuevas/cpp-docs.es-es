---
title: /validate/charset (Validar los caracteres compatibles)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: 2390aa98b9416eb538f529c8c370c888cccf4734
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498169"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate/charset (Validar los caracteres compatibles)

Valida que el texto del archivo de código fuente solo contenga caracteres que se representen como UTF-8.

## <a name="syntax"></a>Sintaxis

```
/validate-charset[-]
```

## <a name="remarks"></a>Comentarios

Puede usar la opción **/Validate-charset** para validar que el código fuente solo contiene caracteres que se pueden representar en el juego de caracteres de origen y en el juego de caracteres de ejecución. Esta comprobación se habilita automáticamente cuando se especifican las opciones del compilador **/source-charset**, **/Execution-charset**o **/UTF-8** . Puede deshabilitar explícitamente esta comprobación especificando la opción **/Validate-charset-** .

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de código fuente se encuentra en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de código fuente se codifica mediante la página de códigos del usuario actual, a menos que haya especificado una página de códigos mediante **/UTF-8** o la opción **/source-charset** . Visual Studio permite guardar el código fuente C++ mediante el uso de varias codificaciones de caracteres. Para obtener información sobre los juegos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje. Para obtener una lista de identificadores de páginas de códigos y nombres de juegos de caracteres compatibles, vea identificadores de [páginas de códigos](/windows/win32/Intl/code-page-identifiers).

Visual Studio usa UTF-8 como codificación de caracteres interna durante la conversión entre el juego de caracteres de origen y el juego de caracteres de ejecución. Si un carácter del archivo de código fuente no se puede representar en el juego de caracteres de ejecución, la conversión UTF-8 sustituye un signo de interrogación '? '. La opción **/Validate-charset** hace que la compilación notifique una advertencia si esto ocurre.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda las **propiedades de configuración**, la carpeta de línea de **comandos** **C/C++** ,.

1. En **opciones adicionales**, agregue la opción **/Validate-charset** y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (establecer juego de caracteres de ejecución)](execution-charset-set-execution-character-set.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
