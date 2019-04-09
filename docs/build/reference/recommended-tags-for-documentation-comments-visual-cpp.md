---
title: Etiquetas recomendadas para comentarios de documentación (comentarios de documentación de C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 2a6a2c3983c10579a6cd96b69be81aa7df8b8ee7
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59027901"
---
# <a name="recommended-tags-for-documentation-comments"></a>Etiquetas recomendadas para los comentarios de documentación

El compilador de MSVC procesará los comentarios de documentación en el código y crea un archivo .xdc para cada operación de compilación y xdcmake.exe procesará los archivos .xdc en un archivo .xml. El procesamiento del archivo .xml para crear documentación es un detalle que se debe implementar en el sitio.

Las etiquetas se procesan en construcciones como los tipos y miembros de tipo.

Las etiquetas deben preceder inmediatamente a los tipos o miembros.

> [!NOTE]
>  Los comentarios de documentación no se pueden aplicar a un espacio de nombres o en una definición fuera de línea para las propiedades y los eventos; deben estar en las declaraciones de clase.

El compilador procesará cualquier etiqueta que sea un XML válido. Las etiquetas siguientes proporcionan funciones de uso general en la documentación de usuario:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<example>](example-visual-cpp.md)|
|[\<exception>](exception-visual-cpp.md)1|[\<include>](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<param>](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<permission>](permission-visual-cpp.md)1|[\<remarks>](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. El compilador comprueba la sintaxis.

En la versión actual, no se admite el compilador de MSVC `<paramref>`, una etiqueta que sea compatible con otros compiladores de Visual Studio. Visual C++ puede admitir `<paramref>` en una versión futura.

## <a name="see-also"></a>Vea también

[Documentación de XML](xml-documentation-visual-cpp.md)