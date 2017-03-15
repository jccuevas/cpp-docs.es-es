---
title: "Excepciones: Excepciones en los constructores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "constructores [C++], excepciones"
  - "excepciones, en constructores"
  - "producir excepciones, en constructores"
ms.assetid: a78eae5a-5821-4b27-9478-1436320ed1e1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Excepciones: Excepciones en los constructores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al iniciar una excepción en un constructor, limpiar los objetos y asignaciones de memoria ha creado antes de iniciar la excepción, como se explica en [Excepciones: Excepciones que produce de las funciones de The Own](../mfc/exceptions-throwing-exceptions-from-your-own-functions.md).  
  
 Al iniciar una excepción en un constructor, la memoria del propio objeto se ha asignado ya en el momento de llamar al constructor.  Por lo tanto, el compilador automáticamente desasignará la memoria ocupada por el objeto después de que se produzca la excepción.  
  
 Para obtener más información, vea [Excepciones: Liberar objetos de Excepciones](../mfc/exceptions-freeing-objects-in-exceptions.md).  
  
## Vea también  
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)