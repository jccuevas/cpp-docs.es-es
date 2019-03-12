---
title: Etiquetas recomendadas para comentarios de documentación (Visual C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 154cb36ca121fee8731ac4e71506f562abb79988
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/11/2019
ms.locfileid: "57744800"
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>Etiquetas recomendadas para comentarios de documentación (Visual C++)

El compilador de Visual C++ procesará los comentarios de documentación en el código y crea un archivo .xdc para cada compilando, y xdcmake.exe procesará los archivos .xdc en un archivo .xml. El procesamiento del archivo .xml para crear documentación es un detalle que se debe implementar en el sitio.

Las etiquetas se procesan en construcciones como los tipos y miembros de tipo.

Las etiquetas deben preceder inmediatamente a los tipos o miembros.

> [!NOTE]
>  Los comentarios de documentación no se pueden aplicar a un espacio de nombres o en una definición fuera de línea para las propiedades y los eventos; deben estar en las declaraciones de clase.

El compilador procesará cualquier etiqueta que sea un XML válido. Las etiquetas siguientes proporcionan funciones de uso general en la documentación de usuario:

||||
|-|-|-|
|[\<c>](../ide/c-visual-cpp.md)|[\<code>](../ide/code-visual-cpp.md)|[\<example>](../ide/example-visual-cpp.md)|
|[\<exception>](../ide/exception-visual-cpp.md)1|[\<include>](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|
|[\<para>](../ide/para-visual-cpp.md)|[\<param>](../ide/param-visual-cpp.md)1|[\<paramref>](../ide/paramref-visual-cpp.md)1|
|[\<permission>](../ide/permission-visual-cpp.md)1|[\<remarks>](../ide/remarks-visual-cpp.md)|[\<returns>](../ide/returns-visual-cpp.md)|
|[\<see>](../ide/see-visual-cpp.md)1|[\<seealso>](../ide/seealso-visual-cpp.md)1|[\<summary>](../ide/summary-visual-cpp.md)|
|[\<value>](../ide/value-visual-cpp.md)|||

1. El compilador comprueba la sintaxis.

En la versión actual, el compilador de Visual C++ no admite `<paramref>`, una etiqueta compatible con otros compiladores de Visual Studio. Visual C++ puede admitir `<paramref>` en una versión futura.

## <a name="see-also"></a>Vea también

[Documentación de XML](../ide/xml-documentation-visual-cpp.md)
