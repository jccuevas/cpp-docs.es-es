---
title: Etiquetas recomendadas para comentarios de documentación (Visual C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1b25ad029a59c4b23bcab093b3742f16f7ca9175
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "33328625"
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