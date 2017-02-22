---
title: "CString Exception Cleanup | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CString objects, excepciones"
  - "control de excepciones, cleanup code"
ms.assetid: 28b9ce70-be63-4a0d-92a8-44bbfbc95e83
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CString Exception Cleanup
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En versiones anteriores de MFC, es importante que se limpian uso posterior de los objetos de [CString](../atl-mfc-shared/reference/cstringt-class.md) .  Con la versión 3,0 de MFC y limpieza posterior, explícita ya no es necesario.  
  
 Bajo el mecanismo de control de excepciones de C\+\+ que MFC utiliza ahora, no tiene que preocuparse de limpieza después de una excepción.  Para obtener una descripción de cómo C\+\+ “desenredo” la pila después de que se detecte una excepción, vea [el intento, captura, y los extractos throw](../cpp/try-throw-and-catch-statements-cpp.md).  Aunque use las macros MFC **TRY**\/de**CATCH** en lugar de las palabras clave **try** y **catch**de C\+\+, MFC utiliza el mecanismo de excepciones de C\+\+ en, por lo que no debe limpiar explícitamente.  
  
## Vea también  
 [Cadenas](../atl-mfc-shared/strings-atl-mfc.md)   
 [Control de excepciones](../mfc/exception-handling-in-mfc.md)