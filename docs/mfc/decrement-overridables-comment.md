---
title: "// Overridables (Comentario) | Microsoft Docs"
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
  - "archivos de código fuente MFC, Overridables (comentario)"
  - "comentarios reemplazables en archivos de código fuente MFC"
  - "reemplazar, comentarios reemplazables en archivos de código fuente MFC"
ms.assetid: 8968dea5-0d94-451f-bcb2-991580e65ba2
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Overridables (Comentario)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sección de `// Overridables` de una declaración de clase MFC contiene funciones virtuales que puede reemplazar en una clase derivada si necesita modificar el comportamiento de la clase base.  Se llama normalmente a partir de " ON ", aunque no es estrictamente necesario.  Las funciones aquí están diseñados para reemplazar y, a menudo implementan o proporcionan algún tipo de “devolución” o “enlace.” Normalmente, protegen estos miembros.  
  
 En MFC, las funciones virtuales puras siempre se almacenan en esta sección.  Una función virtual pura en C\+\+ es una del formulario:  
  
 `virtual void OnDraw( ) = 0;`  
  
 En la lista de clase sample `CStdioFile`, en [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista no incluye ninguna sección de los overridables.  Clase **CDocument**, por otro lado, listas aproximadamente 10 funciones overridable miembro.  
  
 En algunas clases, también puede ver el comentario `// Advanced Overridables`.  Estas son las funciones que solo los desarrolladores avanzados deben intentar reemplazar.  Probablemente nunca necesitará reemplazarlas.  
  
> [!NOTE]
>  Las convenciones descritas en este caso también funcionan bien, normalmente para los métodos y propiedades de automatización \(conocida como antes automatización OLE\).  Los métodos de automatización son similares a las operaciones de MFC.  Las propiedades de automatización son similares a los atributos de MFC.  Los eventos de automatización \(compatibles con los controles ActiveX, antes conocido como controles OLE\) son similares a las funciones overridable miembro MFC.  
  
## Vea también  
 [Usar los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [\/\/ Implementation \(Comentario\)](../mfc/decrement-implementation-comment.md)   
 [\/\/ Constructors \(Comentario\)](../mfc/decrement-constructors-comment.md)   
 [\/\/ Attributes \(Comentario\)](../mfc/decrement-attributes-comment.md)   
 [\/\/ Operations \(Comentario\)](../mfc/decrement-operations-comment.md)