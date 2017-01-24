---
title: "// Constructors (Comentario) | Microsoft Docs"
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
  - "comentarios, constructors (comentario)"
  - "comentarios, MFC"
  - "constructores [C++], declarar"
  - "constructors (comentario)"
  - "declaraciones, constructores"
  - "declarar constructores, comentarios en código"
  - "constructores de instancias, comentarios en código"
  - "archivos de código fuente MFC, Constructors (comentario)"
ms.assetid: f400774e-ba85-49ed-85b7-70ef2f7dcb2b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# // Constructors (Comentario)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La sección de `// Constructors` de una declaración de clase MFC declara constructores \(en el sentido de C\+\+\) así como cualquier función de inicialización necesaria utilizar realmente el objeto.  Por ejemplo, `CWnd::Create` está en la sección de los constructores porque antes de utilizar el objeto de `CWnd` , debe ser “construido totalmente” por la primera llamada al constructor de C\+\+ y después llamar a la función de **crear** .  Normalmente, estos miembros son públicos.  
  
 Por ejemplo, la clase que `CStdioFile` tiene tres constructores, uno de los cuales se muestran en la lista en [Un ejemplo de los comentarios](../mfc/an-example-of-the-comments.md).  
  
## Vea también  
 [Usar los archivos de código fuente de MFC](../mfc/using-the-mfc-source-files.md)   
 [\/\/ Implementation \(Comentario\)](../mfc/decrement-implementation-comment.md)   
 [\/\/ Attributes \(Comentario\)](../mfc/decrement-attributes-comment.md)   
 [\/\/ Operations \(Comentario\)](../mfc/decrement-operations-comment.md)   
 [\/\/ Overridables \(Comentario\)](../mfc/decrement-overridables-comment.md)