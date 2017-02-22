---
title: "Trabajar con objetos Window | Microsoft Docs"
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
  - "ventanas secundarias, trabajar con"
  - "Window (objetos), trabajar con"
ms.assetid: f73aa254-90e3-46a9-8e9b-d78b7054a331
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Trabajar con objetos Window
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Trabajar con las llamadas de las ventanas para dos clases de actividad:  
  
-   Controlar mensajes de Windows  
  
-   Dibuja en la ventana  
  
 Para controlar los mensajes de Windows en cualquier ventana, incluidos dispone de las ventanas secundarias, vea [Asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md) para asignar los mensajes a la clase de ventana de C\+\+.  Escriba las funciones miembro de controladores de mensajes en la clase.  
  
 El gráfico en una aplicación de .NET framework aparece en la vista, cuya se denomina función miembro de [OnDraw](../Topic/CView::OnDraw.md) siempre que el contenido de la ventana se deben dibujados.  Si la ventana es un elemento secundario de la vista, es posible que delega algo de dibujo de la vista a la ventana secundaria teniendo una llamada de `OnDraw` de las funciones miembro de la ventana.  
  
 En cualquier caso, necesitará un contexto para dibujar.  Puede utilizar el lápiz común, el pincel, y otros objetos gráficos contenidos en el contexto de dispositivo asociado a la ventana.  O puede modificar estos objetos para obtener los efectos de dibujo que necesita.  Con el contexto de dispositivo configurar como desee, llame a de las funciones miembro de clases [CDC](../mfc/reference/cdc-class.md) \(clase de dispositivo\- contexto\) para dibujar líneas, formas, y el texto; para utilizar colores; y para trabajar con un sistema de coordenadas.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Control de mensajes y asignación](../mfc/message-handling-and-mapping.md)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Objetos gráficos](../mfc/graphic-objects.md)  
  
## Vea también  
 [Window \(Objetos\)](../mfc/window-objects.md)