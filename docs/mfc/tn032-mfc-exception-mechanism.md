---
title: "TN032: Mecanismo de excepciones de MFC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.exceptions"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CException (clase), utilizar"
  - "MFC, excepciones"
  - "TN032"
ms.assetid: 0271f0aa-82cb-47a2-b7ea-e88126fc7e43
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# TN032: Mecanismo de excepciones de MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las versiones anteriores de Visual C\+\+ no admitidos el mecanismo estándar de excepciones de C\+\+, y MFC proporcionaba macros **TRY\/CATCH\/THROW** utilizadas en su lugar.  Esta versión de Visual C\+\+ admite todas las excepciones de C\+\+.  Esta nota se han tratado algunos detalles de implementación avanzada de las macros anteriores como automáticamente objetos basados en pila de limpieza.  Dado que la pila de soporte de excepciones de C\+\+ que desenredo de forma predeterminada, esta nota técnica ya no es necesaria.  
  
 Hace referencia a [Excepciones: Utilizando las macros y C\+\+ Excepciones de MFC](../mfc/exceptions-using-mfc-macros-and-cpp-exceptions.md) para obtener más información sobre las diferencias entre macros de MFC y las nuevas palabras clave de C\+\+.  
  
## Vea también  
 [Notas técnicas por número](../mfc/technical-notes-by-number.md)   
 [Notas técnicas por categoría](../mfc/technical-notes-by-category.md)