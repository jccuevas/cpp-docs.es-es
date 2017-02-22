---
title: "Implementar las &#225;reas de trabajo en los controles de lista | Microsoft Docs"
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
  - "controles de lista, áreas de trabajo"
  - "áreas de trabajo en control de lista"
ms.assetid: fbbb356b-3359-4348-8603-f1cb114cadde
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Implementar las &#225;reas de trabajo en los controles de lista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, un control de lista organiza todos los elementos de un modo estándar de la cuadrícula.  Sin embargo, se admiten otro método, zonas de trabajo, que organiza los elementos de lista en grupos rectangulares.  Para una imagen de un control de lista que implemente zonas de trabajo, vea Controles de vista de lista de Utilizar en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
> [!NOTE]
>  Las zonas de trabajo solo pueden verse cuando el control de lista está en icono o pequeño para el icono.  Sin embargo, se mantiene una zona de trabajo actual si la vista se cambia al informe o el modo enumerado.  
  
 Las zonas de trabajo se pueden utilizar para mostrar un borde vacío \(en el izquierdo, superior y derecho de elementos\), o produce una barra de desplazamiento horizontal que se mostrará cuando no haya ningún normalmente una.  Otro uso común es crear zonas de trabajo varias a qué elementos se pueden mover o quitar.  Con este método, se podría crear áreas en una vista única que tienen significados diferentes.  El usuario podría a clasificar los elementos colocándolos en otra área.  Un ejemplo de esto sería una vista de un sistema de archivos que tiene un área para los archivos de lectura\/escritura y otra área para los archivos de solo lectura.  Si un elemento file fuera movido al área de solo lectura, automáticamente protegió a ser de sólo lectura.  Mover un archivo de sólo lectura en el área de lectura y escritura crear la escritura del archivo.  
  
 `CListCtrl` proporciona varias funciones miembro para crear y administrar zonas de trabajo en el control de lista.  [GetWorkAreas](../Topic/CListCtrl::GetWorkAreas.md) y [SetWorkAreas](../Topic/CListCtrl::SetWorkAreas.md) recupera y establece una matriz de los objetos de `CRect` \(o de las estructuras de `RECT` \), que almacenan las zonas de trabajo actualmente implementadas para el control de lista.  Además, [GetNumberOfWorkAreas](../Topic/CListCtrl::GetNumberOfWorkAreas.md) recupera el número actual de zonas de trabajo para el control de lista \(de forma predeterminada, cero\).  
  
## Elementos y zonas de trabajo  
 Cuando se crea un área de trabajo, los elementos que mienten dentro de la zona de trabajo se convierten en miembros de ella.  De igual forma, si un elemento se mueve a un área de trabajo, se convierte en un miembro de la zona de trabajo a la que se ha movido.  Si un elemento no se encuentra dentro de una zona de trabajo, automáticamente se convierte en un miembro de la primera \(índice 0\) área de trabajo.  Si desea crear un elemento y haga colocar dentro de una zona de trabajo concreta, necesitará crear el elemento y después mover esa a la zona de trabajo deseada con una llamada a [SetItemPosition](../Topic/CListCtrl::SetItemPosition.md).  El segundo ejemplo siguiente muestra esta técnica.  
  
 El ejemplo siguiente implementa cuatro zonas de trabajo \(`rcWorkAreas`\), el tamaño igual con un borde píxel\- ancho 10 alrededor de cada área de trabajo, en un control de lista \(`m_WorkAreaListCtrl`\).  
  
 [!code-cpp[NVC_MFCControlLadenDialog#20](../mfc/codesnippet/CPP/implementing-working-areas-in-list-controls_1.cpp)]  
  
 La llamada a [ApproximateViewRect](../Topic/CListCtrl::ApproximateViewRect.md) se hizo para obtener una estimación de la superficie total necesaria para mostrar todos los elementos de una región.  Esta estimación se divide en cuatro regiones y se completa con un borde píxel\- ancho 5.  
  
 El ejemplo siguiente se asigna los elementos de lista existentes a cada grupo \(`rcWorkAreas`\) y actualiza la vista de control \(`m_``WorkAreaListCtrl`\) para rellenar el efecto.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#21](../mfc/codesnippet/CPP/implementing-working-areas-in-list-controls_2.cpp)]  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)