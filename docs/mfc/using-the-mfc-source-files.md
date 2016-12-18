---
title: "Usar los archivos de c&#243;digo fuente de MFC | Microsoft Docs"
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
  - "comentarios, MFC"
  - "archivos de código fuente MFC"
  - "MFC, archivos de código fuente"
  - "obtener acceso a miembro privado"
  - "obtener acceso a miembro protegido"
  - "miembros públicos"
  - "archivos de código fuente"
  - "archivos de código fuente, MFC"
ms.assetid: 3230e8fb-3b69-4ddf-9538-365ac7ea5e72
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar los archivos de c&#243;digo fuente de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El código fuente completo de la biblioteca de \(MFC\) de la clase de la Microsoft foundation class.  Archivos de encabezado \(.h\) está en el directorio del \\atlmfc\\include; los archivos de implementación \(.cpp\) están en el directorio de \\atlmfc\\src\\mfc.  
  
 Esta familia de casos explica convenciones que utiliza MFC para comentar las distintas partes de cada clase, lo medio de estos comentarios, y lo que debe saber para buscar en cada sección.  Los asistentes de Visual C\+\+ utilizan convenciones similares para las clases que crea automáticamente, y encontrará probablemente a estas convenciones útiles para el propio código.  
  
 Puede que esté familiarizado con **público**, `protected`, y las palabras clave de `private` C\+\+.  Al examinar los archivos de encabezado de MFC, encontrará que cada clase puede tener varios de cada uno de ellos.  Por ejemplo, las variables miembro y las funciones públicas podrían estar en más de una palabra clave de **público** .  Esto es porque MFC separa las variables miembro y las funciones basándose en su uso, no por el tipo de acceso permitido.  MFC utiliza `private` moderación; incluso los elementos consideró los detalles de la implementación se protegen normalmente y muchas veces son públicas.  Aunque el acceso a los detalles de la implementación se desaliente, MFC permite la decisión.  
  
 En los archivos de código fuente de MFC y los archivos que el asistente para aplicaciones MFC crea, encontrará comentarios como estas dentro de declaraciones de clase \(normalmente en el orden indicado\):  
  
 `// Constructors`  
  
 `// Attributes`  
  
 `// Operations`  
  
 `// Overridables`  
  
 `// Implementation`  
  
 Temas cubiertos en esta familia de son los artículos:  
  
-   [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)  
  
-   [El comentario de la implementación de \/\/](../mfc/decrement-implementation-comment.md)  
  
-   [El comentario de \/\/Constructores](../mfc/decrement-constructors-comment.md)  
  
-   [El comentario de los atributos de \/\/](../mfc/decrement-attributes-comment.md)  
  
-   [El comentario de las operaciones de \/\/](../mfc/decrement-operations-comment.md)  
  
-   [El comentario de \/\/Overridables](../mfc/decrement-overridables-comment.md)  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)