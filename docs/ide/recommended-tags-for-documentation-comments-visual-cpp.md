---
title: "Etiquetas recomendadas para comentarios de documentaci&#243;n (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Etiquetas recomendadas para comentarios de documentaci&#243;n (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El compilador de Visual C\+\+ procesará comentarios de documentación en el código y crea un archivo .xdc para cada compilación, y xdcmake.exe procesará archivos .xdc a un archivo .xml.  Procesar el archivo .xml para crear documentación es un detalle que necesita implementar en el sitio.  
  
 Las etiquetas se procesan en estructuras como tipos y miembros de tipo.  
  
 Las etiquetas deben inmediatamente anterior a tipos o miembros.  
  
> [!NOTE]
>  Los comentarios de documentación no se pueden aplicar a un espacio de nombres o en fuera de la definición de la línea de propiedades y eventos; los comentarios de documentación deben en las declaraciones de la en\-clase.  
  
 El compilador procesará cualquier etiqueta válida en XML.  Las etiquetas siguientes proporcionan funcionalidad de uso frecuente en la documentación de usuario:  
  
||||  
|-|-|-|  
|[\<c\>](../ide/c-visual-cpp.md)|[\<code\>](../ide/code-visual-cpp.md)|[\<example\>](../ide/example-visual-cpp.md)|  
|[\<exception\>](../ide/exception-visual-cpp.md)1|[\<include\>](../ide/include-visual-cpp.md)1|[\<list\>](../ide/list-visual-cpp.md)|  
|[\<para\>](../ide/para-visual-cpp.md)|[\<param\>](../ide/param-visual-cpp.md)1|[\<paramref\>](../ide/paramref-visual-cpp.md)1|  
|[\<permission\>](../ide/permission-visual-cpp.md)1|[\<remarks\>](../ide/remarks-visual-cpp.md)|[\<returns\>](../ide/returns-visual-cpp.md)|  
|[\<see\>](../ide/see-visual-cpp.md)1|[\<seealso\>](../ide/seealso-visual-cpp.md)1|[\<summary\>](../ide/summary-visual-cpp.md)|  
|[\<value\>](../ide/value-visual-cpp.md)|||  
  
 1.  El compilador comprueba sintaxis.  
  
 En la versión actual, el compilador de Visual C\+\+ no admite `<paramref>`, una etiqueta admitida por otros compiladores de Visual Studio.  Visual C\+\+ puede admitir `<paramref>` en futuras versiones.  
  
## Vea también  
 [Documentación de XML](../ide/xml-documentation-visual-cpp.md)