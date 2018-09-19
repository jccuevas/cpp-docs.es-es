---
title: -origen-charset (establecer el juego de caracteres origen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
f1_keywords:
- source-charset
- /source-charset
dev_langs:
- C++
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c36f898c005a989a7be78e436b560fe9a0536b57
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45715070"
---
# <a name="source-charset-set-source-character-set"></a>/ Source-CharSet (establecer juego de caracteres de origen)

Le permite especificar el juego para el ejecutable de caracteres de origen.

## <a name="syntax"></a>Sintaxis

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Argumentos

**IANA_name**<br/>
Asigne el carácter definido por la IANA.

**CPID**<br/>
El identificador de la página de código como un número decimal.

## <a name="remarks"></a>Comentarios

Puede usar el **/Source-CharSet** opción para especificar un carácter extendido origen configurado para usar cuando los archivos de origen incluyen caracteres que no están representados en el juego de caracteres básico de origen. El juego de caracteres de origen es la codificación usada para interpretar el texto de origen del programa en la representación interna que se usa como entrada para las fases de preprocesamiento antes de la compilación. La representación interna, a continuación, se convierte en el juego de caracteres de ejecución para almacenar valores de cadena y carácter en el archivo ejecutable. Puede usar cualquier la IANA o juego de caracteres ISO o un punto (.) seguido por un identificador de página de código decimal de 3 a 5 dígitos para especificar el juego de caracteres que utilice. Para obtener una lista de admite identificadores de páginas de código y juego de caracteres de nombres, vea [identificadores de páginas de código](/windows/desktop/Intl/code-page-identifiers).

De forma predeterminada, Visual Studio detecta una marca de orden de bytes para determinar si el archivo de origen está en un formato codificado de Unicode, por ejemplo, UTF-16 o UTF-8. Si no se encuentra ninguna marca de orden de bytes, se supone que el archivo de origen se codifica utilizando la página de códigos del usuario actual, a menos que especifique un juego de caracteres nombre o página de códigos mediante el uso de la **/Source-CharSet** opción. Visual Studio le permite guardar el código fuente de C++ mediante cualquiera de las varias codificaciones de caracteres. Para obtener más información acerca de los juegos de caracteres de origen y ejecución, consulte [juegos de caracteres](../../cpp/character-sets.md) en la documentación del lenguaje.

El juego de caracteres de origen que proporcione debe asignar los caracteres ASCII de 7 bits a los mismos puntos de código en el juego de caracteres o puedan seguir muchos errores de compilación. El juego de caracteres de origen también debe ser asignable al conjunto puedan codificar con UTF-8 de caracteres de Unicode extendido. Caracteres que no se puedan codificar con UTF-8 se representan mediante un sustituto específico de la implementación. El compilador de Microsoft usa un signo de interrogación para estos caracteres.

Si desea establecer el juego de caracteres de origen y el juego de caracteres de ejecución en UTF-8, puede usar el **/UTF-8** opción del compilador como un acceso directo. Equivale a especificar **/source-charset:utf-/execution 8-charset:utf-8** en la línea de comandos. Cualquiera de estas opciones también habilita la **/Validate/CharSet** opción predeterminada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades de proyecto](../../ide/working-with-project-properties.md).

1. Expanda el **propiedades de configuración**, **C o C++**, **línea de comandos** carpeta.

1. En **opciones avanzadas**, agregue el **/Source-CharSet** opción y especifique la codificación preferida.

1. Elija **Aceptar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)<br/>
[/ Execution-CharSet (establecer juego de caracteres de ejecución)](../../build/reference/execution-charset-set-execution-character-set.md)
[/UTF-8 (establecer origen y ejecutable juegos a UTF-8 de caracteres)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
 [ /Validate/CharSet (validar compatible caracteres)](../../build/reference/validate-charset-validate-for-compatible-characters.md)