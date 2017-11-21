---
title: "Etiquetas recomendadas para comentarios de documentación (Visual C++) | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65d2161edc4b2aa03cd547467ca0f38158850051
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>Etiquetas recomendadas para comentarios de documentación (Visual C++)
El compilador de Visual C++ procesará los comentarios de documentación en el código y crea un archivo .xdc por cada operación de compilación y xdcmake.exe procesará los archivos .xdc en un archivo XML. Procesar el archivo .xml para crear documentación es un detalle que debe implementarse en el sitio.  
  
 Las etiquetas se procesan en construcciones, como tipos y miembros de tipo.  
  
 Etiquetas deben preceder inmediatamente a tipos o miembros.  
  
> [!NOTE]
>  Los comentarios de documentación no se pueden aplicar a un espacio de nombres o en fuera de la definición de línea para las propiedades y eventos. los comentarios de documentación deben en las declaraciones de clase.  
  
 El compilador procesará cualquier etiqueta que sea un XML válido. Las siguientes etiquetas proporcionan funcionalidad utilizada en la documentación de usuario:  
  
||||  
|-|-|-|  
|[\<c>](../ide/c-visual-cpp.md)|[\<code>](../ide/code-visual-cpp.md)|[\<example>](../ide/example-visual-cpp.md)|  
|[\<excepción >](../ide/exception-visual-cpp.md)1|[\<Incluir >](../ide/include-visual-cpp.md)1|[\<list>](../ide/list-visual-cpp.md)|  
|[\<para>](../ide/para-visual-cpp.md)|[\<param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|  
|[\<permiso >](../ide/permission-visual-cpp.md)1|[\<remarks>](../ide/remarks-visual-cpp.md)|[\<returns>](../ide/returns-visual-cpp.md)|  
|[\<Consulte >](../ide/see-visual-cpp.md)1|[\<seealso >](../ide/seealso-visual-cpp.md)1|[\<summary>](../ide/summary-visual-cpp.md)|  
|[\<value>](../ide/value-visual-cpp.md)|||  
  
 1. Compilador comprueba la sintaxis.  
  
 En la versión actual, el compilador de Visual C++ no admite `<paramref>`, una etiqueta que sea compatible con otros compiladores de Visual Studio. Visual C++ pueden admitir `<paramref>` en una versión futura.  
  
## <a name="see-also"></a>Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)