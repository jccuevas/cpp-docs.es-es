---
title: "// Implementation (Comentario) | Microsoft Docs"
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
helpviewer_keywords: 
  - "comentarios, Implementation (comentarios)"
  - "comentarios, MFC"
  - "comentario Implementation en archivos de código fuente MFC"
  - "archivos de código fuente MFC, Implementation (comentario)"
ms.assetid: 4d799c07-8e71-4a6b-90ab-8282d6ff48ce
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Implementation (Comentario)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sección de `// Implementation` es la parte más importante de cualquier declaración de clases MFC.  
  
 Casas de esta sección todos los detalles de la implementación.  Las variables miembro y las funciones miembro pueden aparecer en esta sección.  Todo bajo esta línea podría cambiar en futuras versiones de MFC.  A menos que no puede evitar, no debe confiar en los detalles debajo de la línea de `// Implementation` .  Además, no documentan los miembros declarados bajo la línea de la implementación, aunque alguna implementación se trate en notas técnicas.  Reemplazos de funciones virtuales en la clase base residen en esta sección, sin importar cuya sección la función de clase base se define en, porque el hecho de que una función reemplace la implementación de la clase base se considera un detalle de implementación.  Normalmente, protegen estos miembros, pero no siempre.  
  
 Aviso de `CStdioFile` que muestra bajo [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md) que los miembros declarados bajo el comentario de `// Implementation` pueden declararse como **público**, `protected`, o `private`.  Debe utilizar sólo a estos miembros con precaución, porque pueden cambiar en el futuro.  Declarar un grupo de miembros como **público** puede ser necesario que la implementación de la biblioteca de clases funcione correctamente.  Sin embargo, esto no significa que puede utilizar con seguridad a los miembros declarados en.  
  
> [!NOTE]
>  Puede encontrar comentarios de los tipos restantes encima o debajo del comentario de `// Implementation` .  En cualquier caso, describen las clases de miembros declarados debajo de ellos.  Si aparecen debajo del comentario de `// Implementation` , debe suponer que pueden cambiar en versiones futuras de MFC.  
  
## Vea también  
 [Usar los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [\/\/ Constructors \(Comentario\)](../mfc/decrement-constructors-comment.md)   
 [\/\/ Attributes \(Comentario\)](../mfc/decrement-attributes-comment.md)   
 [\/\/ Operations \(Comentario\)](../mfc/decrement-operations-comment.md)   
 [\/\/ Overridables \(Comentario\)](../mfc/decrement-overridables-comment.md)