---
title: "Seleccionar un objeto gr&#225;fico en un contexto de dispositivo | Microsoft Docs"
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
  - "contextos de dispositivo, objetos gráficos"
  - "contextos de dispositivo, seleccionar objetos gráficos en"
  - "objetos GDI [C++], contextos de dispositivo"
  - "objetos gráficos, seleccionar en contexto de dispositivo"
  - "duración, objetos gráficos"
  - "SelectObject (método)"
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Seleccionar un objeto gr&#225;fico en un contexto de dispositivo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este tema se aplica al uso de objetos gráficos en el contexto del dispositivo de una ventana.  Después de que se [cree un objeto de dibujo](../mfc/one-stage-and-two-stage-construction-of-objects.md), debe seleccionarlo en el contexto de dispositivo en lugar del objeto predeterminado almacenado allí:  
  
 [!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/CPP/selecting-a-graphic-object-into-a-device-context_1.cpp)]  
  
## Duración de objetos gráficos  
 El objeto gráfico devuelto por [SelectObject](../Topic/CDC::SelectObject.md) es “temporal”. Es decir, se eliminará por la función miembro de [OnIdle](../Topic/CWinApp::OnIdle.md) de la clase `CWinApp` la próxima vez que el programa obtiene tiempos de inactividad.  Mientras utiliza el objeto devuelto por `SelectObject` en una sola función sin devolver el control al bucle principal, no tendrá ningún problema.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Objetos gráficos](../mfc/graphic-objects.md)  
  
-   [Uno\- fase y construcción de dos pasos de objetos gráficos](../mfc/one-stage-and-two-stage-construction-of-objects.md)  
  
-   [Contextos de dispositivo](../mfc/device-contexts.md)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
## Vea también  
 [Objetos gráficos](../mfc/graphic-objects.md)