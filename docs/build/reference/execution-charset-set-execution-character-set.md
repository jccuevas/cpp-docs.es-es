---
title: /Execution-charset (establecer juego de caracteres de ejecución)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 44e83524867bc8a914706e1f5b45b61bc4a48087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492916"
---
# <a name="execution-charset-set-execution-character-set"></a>/Execution-charset (establecer juego de caracteres de ejecución)

Permite especificar el juego de caracteres de ejecución para el ejecutable.

## <a name="syntax"></a>Sintaxis

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Argumentos

*IANA_name*<br/>
Nombre del juego de caracteres definido por IANA.

*CPID*<br/>
Identificador de la página de códigos.

## <a name="remarks"></a>Comentarios

Puede usar la opción **/Execution-charset** para especificar un juego de caracteres de ejecución. El juego de caracteres de ejecución es la codificación que se usa para el texto del programa que se introduce en la fase de compilación después de todos los pasos de preprocesamiento. Este juego de caracteres se utiliza para la representación interna de cualquier literal de cadena o carácter en el código compilado. Establezca esta opción para especificar el juego de caracteres de ejecución extendido que se utilizará cuando los archivos de código fuente incluyan caracteres que no se pueden representar en el juego de caracteres de ejecución básico. Puede usar el nombre del juego de caracteres de IANA o ISO, o un punto (.) seguido de un identificador de página de códigos decimal de 3 a 5 dígitos para especificar el juego de caracteres que se va a usar. Para obtener una lista de identificadores de páginas de códigos y nombres de juegos de caracteres compatibles, vea identificadores de [páginas de códigos](/windows/win32/Intl/code-page-identifiers).

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de código fuente se encuentra en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de código fuente se codifica mediante la página de códigos del usuario actual, a menos que haya especificado un nombre de juego de caracteres o una página de códigos mediante la opción **/source-charset** o la opción **/UTF-8** . Visual Studio permite guardar el código fuente C++ mediante el uso de varias codificaciones de caracteres. Para obtener información sobre los juegos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.

Si desea establecer el juego de caracteres de origen y el juego de caracteres de ejecución en UTF-8, puede usar la opción del compilador **/UTF-8** como método abreviado. Es equivalente a especificar **/source-charset: UTF-8/Execution-charset: UTF-8** en la línea de comandos. Cualquiera de estas opciones también habilita la opción **/Validate-charset** de forma predeterminada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda las **propiedades de configuración**, la carpeta de línea de **comandos** **C/C++** ,.

1. En **opciones adicionales**, agregue la opción **/Execution-charset** y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate/charset (Validar los caracteres compatibles)](validate-charset-validate-for-compatible-characters.md)
