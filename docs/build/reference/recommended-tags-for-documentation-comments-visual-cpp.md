---
title: Etiquetas recomendadas para comentarios de documentación (comentarios de documentación de C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336170"
---
# <a name="recommended-tags-for-documentation-comments"></a>Etiquetas recomendadas para los comentarios de documentación

El compilador MSVC procesará los comentarios de documentación en el código y creará un archivo .xdc para cada compilación, y xdcmake.exe procesará los archivos .xdc en un archivo .xml. El procesamiento del archivo .xml para crear documentación es un detalle que se debe implementar en el sitio.

Las etiquetas se procesan en construcciones como los tipos y miembros de tipo.

Las etiquetas deben preceder inmediatamente a los tipos o miembros.

> [!NOTE]
> Los comentarios de documentación no se pueden aplicar a un espacio de nombres o en una definición fuera de línea para las propiedades y los eventos; deben estar en las declaraciones de clase.

El compilador procesará cualquier etiqueta que sea un XML válido. Las etiquetas siguientes proporcionan funciones de uso general en la documentación de usuario:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<código>](code-visual-cpp.md)|[\<ejemplo>](example-visual-cpp.md)|
|>de excepción 1 [ \< ](exception-visual-cpp.md)|incluyen>1 [ \< ](include-visual-cpp.md)|[\<lista>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|>de parám 1 [ \< ](param-visual-cpp.md)|paramref>1 [ \< ](paramref-visual-cpp.md)|
|permiso>1 [ \< ](permission-visual-cpp.md)|[\<observaciones>](remarks-visual-cpp.md)|[\<devuelve>](returns-visual-cpp.md)|
|ver>1 [ \< ](see-visual-cpp.md)|ver también>1 [ \< ](seealso-visual-cpp.md)|[\<resumen>](summary-visual-cpp.md)|
|[\<>de valor](value-visual-cpp.md)|||

1. El compilador comprueba la sintaxis.

En la versión actual, el `<paramref>`compilador MSVC no admite , una etiqueta que es compatible con otros compiladores de Visual Studio. Visual C++ puede admitir `<paramref>` en una versión futura.

## <a name="see-also"></a>Consulte también

[Documentación XML](xml-documentation-visual-cpp.md)
