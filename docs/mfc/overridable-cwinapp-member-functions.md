---
title: "Funciones miembro de CWinApp que se pueden sobrecargar | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CWinApp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clase de aplicación"
  - "CWinApp (clase), se pueden sobrecargar"
  - "reemplazar, funciones que se pueden sobrecargar en CWinApp"
ms.assetid: 07183d5e-734b-45d9-a8b6-9dde4adac0b4
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Funciones miembro de CWinApp que se pueden sobrecargar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[CWinApp](../mfc/reference/cwinapp-class.md) proporciona varias funciones overridable clave de miembro \(`CWinApp` invalida estos miembros de la clase [CWinThread](../mfc/reference/cwinthread-class.md), que `CWinApp` deriva\):  
  
-   [InitInstance](../mfc/initinstance-member-function.md)  
  
-   [Ejecutar](../mfc/run-member-function.md)  
  
-   [ExitInstance](../mfc/exitinstance-member-function.md)  
  
-   [OnIdle](../mfc/onidle-member-function.md)  
  
 La única función miembro de `CWinApp` que debe invalidar es `InitInstance`.  
  
## Vea también  
 [CWinApp: The Application \(Clase\)](../mfc/cwinapp-the-application-class.md)