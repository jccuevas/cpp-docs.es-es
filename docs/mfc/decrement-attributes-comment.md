---
title: "// Attributes (Comentario) | Microsoft Docs"
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
  - "comentario Attributes en archivos de código fuente MFC"
  - "comentarios, Attributes"
  - "archivos de código fuente MFC, Attributes comment"
  - "publicar el comentario Attributes"
ms.assetid: 96388e11-42df-4994-aedf-decd152961a7
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Attributes (Comentario)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sección de `// Attributes` de una declaración de clase MFC contiene los atributos públicos \(o propiedades\) del objeto.  Éstas son normalmente variables miembro, o get\/set funciones.  “Get” y funciones “set” pueden o no pueden ser virtuales.  “Get” las funciones son normalmente **const**, porque en la mayoría de los casos no tienen efectos secundarios.  Estos miembros normalmente son públicos; los atributos protegidos y privados se encuentran normalmente en la sección de implementación.  
  
 En la lista de clase sample `CStdioFile`, en [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md), la lista incluye una variable miembro, `m_pStream`.  La clase `CDC` muestra a casi 20 miembros bajo este comentario.  
  
> [!NOTE]
>  Las clases grandes, como `CDC` y `CWnd`, pueden tener en muchos miembros que simplemente enumerando todos los atributos de grupo no agregaría mucho a la claridad.  En estos casos, la biblioteca de clases utiliza otros comentarios como los encabezados para describir aún más los miembros.  Por ejemplo, `CDC` utiliza `// Device-Context Functions`, `// Drawing Tool Functions`, `// Drawing Attribute Functions`, y más.  Los grupos que representan atributos deben seguir la sintaxis habitual descrita anteriormente.  Muchas clases VIEJAS tienen una sección de implementación denominada `// Interface Maps`.  
  
## Vea también  
 [Usar los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)   
 [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md)   
 [\/\/ Implementation \(Comentario\)](../mfc/decrement-implementation-comment.md)   
 [\/\/ Constructors \(Comentario\)](../mfc/decrement-constructors-comment.md)   
 [\/\/ Operations \(Comentario\)](../mfc/decrement-operations-comment.md)   
 [\/\/ Overridables \(Comentario\)](../mfc/decrement-overridables-comment.md)