---
title: / Execution-CharSet (establecer juego de caracteres de ejecución)
ms.date: 11/04/2016
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 3535b60d7aad50f7efc5d1f32726560431ac86a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50663975"
---
# <a name="execution-charset-set-execution-character-set"></a>/ Execution-CharSet (establecer juego de caracteres de ejecución)

Le permite especificar el juego para el ejecutable de caracteres de ejecución.

## <a name="syntax"></a>Sintaxis

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Argumentos

*IANA_name*<br/>
Asigne el carácter definido por la IANA.

*CPID*<br/>
Identificador de la página de códigos.

## <a name="remarks"></a>Comentarios

Puede usar el **/Execution-CharSet** opción para especificar un juego de caracteres de ejecución. El juego de caracteres de ejecución es la codificación utilizada para el texto del programa que se introduce en la fase de compilación después de todo los pasos de preprocesamiento. Este juego de caracteres se utiliza para la representación interna de los literales de cadena o un carácter en el código compilado. Establezca esta opción para especificar el juego de caracteres extendido de ejecución debe usar cuando los archivos de origen incluyen caracteres que no se puede representables en el juego de caracteres de ejecución básico. Puede usar cualquier la IANA o juego de caracteres ISO o un punto (.) seguido por un identificador de página de código decimal de 3 a 5 dígitos para especificar el juego de caracteres que utilice. Para obtener una lista de admite identificadores de páginas de código y juego de caracteres de nombres, vea [identificadores de páginas de código](/windows/desktop/Intl/code-page-identifiers).

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que haya especificado un juego de caracteres nombre o página de códigos mediante el uso de la **/Source-CharSet** opción o el   **/UTF-8** opción. Visual Studio le permite guardar el código fuente de C++ mediante cualquiera de las varias codificaciones de caracteres. Para obtener información acerca de los juegos de caracteres de origen y ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.

Si desea establecer el juego de caracteres de origen y el juego de caracteres de ejecución en UTF-8, puede usar el **/UTF-8** opción del compilador como un acceso directo. Equivale a especificar **/source-charset:utf-/execution 8-charset:utf-8** en la línea de comandos. Cualquiera de estas opciones también habilita la **/Validate/CharSet** opción predeterminada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración**, **C o C++**, **línea de comandos** carpeta.

1. En **opciones avanzadas**, agregue el **/Execution-CharSet** opción y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/source/charset (Establecer el juego de caracteres de origen)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate/charset (Validar los caracteres compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)