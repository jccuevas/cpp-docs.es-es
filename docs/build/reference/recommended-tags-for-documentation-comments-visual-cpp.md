---
title: Etiquetas recomendadas para comentarios deC++ documentación (comentarios de documentación)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 4e0937b79012f65ba136e18ac81f014be23688f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168868"
---
# <a name="recommended-tags-for-documentation-comments"></a>Etiquetas recomendadas para los comentarios de documentación

El compilador MSVC procesará los comentarios de documentación en el código y creará un archivo. xdc para cada operación de compilación y xdcmake. exe procesará los archivos. xdc en un archivo. Xml. El procesamiento del archivo .xml para crear documentación es un detalle que se debe implementar en el sitio.

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
|[\<valor>](value-visual-cpp.md)|||

1. El compilador comprueba la sintaxis.

En la versión actual, el compilador MSVC no admite `<paramref>`, una etiqueta que es compatible con otros compiladores de Visual Studio. Visual C++ puede admitir `<paramref>` en una versión futura.

## <a name="see-also"></a>Consulte también

[Documentación de XML](xml-documentation-visual-cpp.md)
