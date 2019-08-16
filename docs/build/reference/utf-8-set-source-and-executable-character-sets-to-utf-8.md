---
title: /UTF-8 (establecer los juegos de caracteres de origen y de ejecución en UTF-8)
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 1ff0f23ad0758642c73b1b35d6d4dd1be20899cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498179"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/UTF-8 (establecer los juegos de caracteres de origen y de ejecución en UTF-8)

Especifica el juego de caracteres de origen y el juego de caracteres de ejecución como UTF-8.

## <a name="syntax"></a>Sintaxis

```
/utf-8
```

## <a name="remarks"></a>Comentarios

Puede usar la opción **/UTF-8** para especificar los juegos de caracteres de origen y de ejecución como codificados mediante UTF-8. Es equivalente a especificar **/source-charset: UTF-8/Execution-charset: UTF-8** en la línea de comandos. Cualquiera de estas opciones también habilita la opción **/Validate-charset** de forma predeterminada. Para obtener una lista de identificadores de páginas de códigos y nombres de juegos de caracteres compatibles, vea identificadores de [páginas de códigos](/windows/win32/Intl/code-page-identifiers).

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de código fuente se encuentra en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de código fuente se codifica mediante la página de códigos del usuario actual, a menos que haya especificado una página de códigos mediante **/UTF-8** o la opción **/source-charset** . Visual Studio permite guardar el código fuente C++ mediante el uso de varias codificaciones de caracteres. Para obtener información sobre los juegos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda las **propiedades de configuración**, la carpeta de línea de **comandos** **C/C++** ,.

1. En **opciones adicionales**, agregue la opción **/UTF-8** para especificar la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (establecer juego de caracteres de ejecución)](execution-charset-set-execution-character-set.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](source-charset-set-source-character-set.md)<br/>
[/validate/charset (Validar los caracteres compatibles)](validate-charset-validate-for-compatible-characters.md)
