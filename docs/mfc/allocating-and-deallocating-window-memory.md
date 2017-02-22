---
title: "Asignar y desasignar memoria de ventana | Microsoft Docs"
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
  - "asignación de memoria, Window (objetos)"
  - "desasignación de memoria"
  - "desasignación de memoria, memoria de ventana"
  - "almacenamiento para objetos de ventana"
  - "almacenamiento para objetos de ventana, asignar"
  - "Window (objetos), desasignar memoria de"
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Asignar y desasignar memoria de ventana
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

No utilice el operador de C\+\+ **borrar** destruir una ventana o una vista del cuadro.  En su lugar, llame a la función `DestroyWindow`miembro de `CWnd` .  Las ventanas del capítulo, por consiguiente, se deben asignar en el montón con el operador **new**.  Tenga cuidado al asignar las ventanas de marco en el marco de pila o global.  Otras ventanas se deben asignar en el marco de pila siempre que sea posible.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Crear ventanas](../mfc/creating-windows.md)  
  
-   [Secuencia de destrucción ventana](../mfc/window-destruction-sequence.md)  
  
-   [Desasociar un CWnd del HWND](../mfc/detaching-a-cwnd-from-its-hwnd.md)  
  
## Vea también  
 [Destruir objetos Window](../mfc/destroying-window-objects.md)