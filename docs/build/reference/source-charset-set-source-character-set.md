---
title: /Source-charset (establecer el juego de caracteres de origen)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: cd3e4eb3fd305ba6bdd298d18b1edb80f2b98343
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498254"
---
# <a name="source-charset-set-source-character-set"></a>/Source-charset (establecer el juego de caracteres de origen)

Permite especificar el juego de caracteres de origen para el ejecutable.

## <a name="syntax"></a>Sintaxis

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Argumentos

**IANA_name**<br/>
Nombre del juego de caracteres definido por IANA.

**CPID**<br/>
Identificador de la página de códigos como un número decimal.

## <a name="remarks"></a>Comentarios

Puede usar la opción **/source-charset** para especificar un juego de caracteres de código fuente extendido que se utilizará cuando los archivos de código fuente incluyan caracteres que no estén representados en el juego básico de caracteres de código fuente. El juego de caracteres de código fuente es la codificación que se usa para interpretar el texto de origen del programa en la representación interna que se usa como entrada para las fases de preprocesamiento antes de la compilación. A continuación, la representación interna se convierte en el juego de caracteres de ejecución para almacenar valores de cadena y de carácter en el archivo ejecutable. Puede usar el nombre del juego de caracteres de IANA o ISO, o un punto (.) seguido de un identificador de página de códigos decimal de 3 a 5 dígitos para especificar el juego de caracteres que se va a usar. Para obtener una lista de identificadores de páginas de códigos y nombres de juegos de caracteres compatibles, vea identificadores de [páginas de códigos](/windows/win32/Intl/code-page-identifiers).

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de código fuente se encuentra en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de código fuente está codificado mediante la página de códigos del usuario actual, a menos que especifique un nombre del juego de caracteres o una página de códigos mediante la opción **/source-charset** . Visual Studio permite guardar el código fuente C++ mediante el uso de varias codificaciones de caracteres. Para obtener más información sobre los juegos de caracteres de origen y de ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.

El juego de caracteres de origen que suministre debe asignar los caracteres ASCII de 7 bits a los mismos puntos de código del juego de caracteres, o es probable que se sigan muchos errores de compilación. El juego de caracteres de origen también debe ser asignable al Juego de caracteres Unicode extendido que se puede codificar mediante UTF-8. Los caracteres que no se pueden codificar en UTF-8 se representan mediante un sustituto específico de la implementación. El compilador de Microsoft usa un signo de interrogación para estos caracteres.

Si desea establecer el juego de caracteres de origen y el juego de caracteres de ejecución en UTF-8, puede usar la opción del compilador **/UTF-8** como método abreviado. Es equivalente a especificar **/source-charset: UTF-8/Execution-charset: UTF-8** en la línea de comandos. Cualquiera de estas opciones también habilita la opción **/Validate-charset** de forma predeterminada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda las **propiedades de configuración**, la carpeta de línea de **comandos** **C/C++** ,.

1. En **opciones adicionales**, agregue la opción **/source-charset** y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (establecer juego de caracteres de ejecución)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate/charset (Validar los caracteres compatibles)](validate-charset-validate-for-compatible-characters.md)
