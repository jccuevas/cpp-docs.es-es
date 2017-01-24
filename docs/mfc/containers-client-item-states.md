---
title: "Contenedores: Estados de elementos de cliente | Microsoft Docs"
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
  - "elementos de cliente y contenedores OLE"
  - "duración, estados de duración y elementos de cliente del contenedor OLE"
  - "contenedores OLE, estados de elementos de cliente"
  - "estados, contenedor OLE de elementos cliente"
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores: Estados de elementos de cliente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica los diferentes estados que un elemento de cliente pasa a lo largo de su duración.  
  
 Un elemento de cliente pasa con varios estados mientras se crea, se activa, se modifica, y se guarda.  Cada vez que cambia de estado del elemento, el marco de trabajo llama [COleClientItem::OnChange](../Topic/COleClientItem::OnChange.md) con la notificación de `OLE_CHANGED_STATE` .  El segundo parámetro es un valor de enumeración de **COleClientItem::ItemState** .  Puede ser:  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 En el estado vacía, un elemento de cliente aún no están completamente un elemento.  La memoria se ha asignado para él, pero todavía no se ha inicializado con los datos de OLE del elemento.  Éste es el estado que un elemento de cliente está en cuando se ha creado con una llamada a **new** pero que no ha experimentado el segundo paso de la creación de dos pasos típica.  
  
 En el segundo paso, realizaba con una llamada a `COleClientItem::CreateFromFile` o a otra función de **CreateFrom***xxxx* , se crea el elemento completamente.  Los datos OLE \(de un archivo o de otro origen, como el portapapeles\) se ha asociado a `COleClientItem`\- objeto derivado.  Ahora el elemento está en el estado cargado.  
  
 Cuando un elemento se ha abierto en la ventana de servidor en lugar de abierto en el lugar en el documento de contenedor, está en \(o abra totalmente\) el estado abierto.  En este estado, una marca de rayitas cruzadas se dibuja normalmente sobre la representación del elemento en la ventana contenedora para indicar que el elemento está activo en otra parte.  
  
 Cuando un elemento se ha producido en contexto, pasa, normalmente sólo brevemente, a través del estado activo.  A continuación entra en el estado activo de la interfaz de usuario, en la que el servidor ha combinado sus menús, barras de herramientas, y otros componentes de la interfaz de usuario con el contenedor.  La presencia de estos componentes de la interfaz de usuario distingue el estado activo de la interfaz de usuario del estado activo.  Si no, el estado activo se parece al estado activo de la interfaz de usuario.  Si el servidor admite deshacer, requieren conservar la información de la fase de reversión\- provincia de elemento OLE hasta alcanzar haber cargado o abra el servidor estado.  
  
## Vea también  
 [Contenedores](../mfc/containers.md)   
 [Activación](../mfc/activation-cpp.md)   
 [Contenedores: Notificaciones de elementos de cliente](../mfc/containers-client-item-notifications.md)   
 [Seguimiento](../mfc/trackers.md)   
 [CRectTracker Class](../mfc/reference/crecttracker-class.md)