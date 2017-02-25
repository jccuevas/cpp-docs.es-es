---
title: "Arrastrar y colocar: Implementar un origen de colocaci&#243;n | Microsoft Docs"
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
  - "arrastrar y colocar, llamar a DoDragDrop"
  - "arrastrar y colocar, colocar origen"
  - "arrastrar y colocar, inicializar operaciones de arrastrar"
  - "funciones OLE de arrastrar y colocar, llamar a DoDragDrop"
  - "funciones OLE de arrastrar y colocar, colocar origen"
  - "funciones OLE de arrastrar y colocar, inicializar operaciones de arrastrar"
ms.assetid: 0ed2fda0-63fa-4b1e-b398-f1f142f40035
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Arrastrar y colocar: Implementar un origen de colocaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo obtener la aplicación para proporcionar datos a una operación de arrastrar y colocar.  
  
 La implementación básica de un origen de posición es relativamente simple.  El primer paso es determinar qué inicio de los eventos una operación de arrastre.  Las instrucciones recomendados de la interfaz de usuario definen el principio de una operación de arrastre como la selección de datos y un evento de `WM_LBUTTONDOWN` que aparecen en un dentro de punto los datos seleccionados.  Los ejemplos [OCLIENT](../top/visual-cpp-samples.md) y [HIERSVR](../top/visual-cpp-samples.md) MFC OLE siguen estas instrucciones.  
  
 Si la aplicación es un contenedor y los datos seleccionado es haber vinculado o un objeto incrustado de `COleClientItem`escrito, llame a su función miembro de `DoDragDrop` .  Si no, cree un objeto de `COleDataSource` , inicialícela con la selección, llame a la función miembro de `DoDragDrop` del objeto de origen de datos.  Si la aplicación es el servidor, utilice `COleServerItem::DoDragDrop`.  Para obtener información sobre cómo personalizar el comportamiento de arrastrar y colocar estándar, vea el artículo [Arrastrar y colocar: El personalizar](../mfc/drag-and-drop-customizing.md).  
  
 Si `DoDragDrop` devuelve `DROPEFFECT_MOVE`, elimine los datos de origen del documento de origen inmediatamente.  Ningún otro valor devuelto de `DoDragDrop` tiene cualquier efecto en un origen de colocación.  
  
 Para obtener más información, vea:  
  
-   [Implementar un destino](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Personalizar arrastrar y colocar](../mfc/drag-and-drop-customizing.md)  
  
-   [La creación y objetos de datos de OLE y orígenes de datos de Destruir](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Objetos de datos y orígenes de datos de OLE de manipulación](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## Vea también  
 [Arrastrar y colocar \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDataSource::DoDragDrop](../Topic/COleDataSource::DoDragDrop.md)   
 [COleClientItem::DoDragDrop](../Topic/COleClientItem::DoDragDrop.md)   
 [CView::OnDragLeave](../Topic/CView::OnDragLeave.md)