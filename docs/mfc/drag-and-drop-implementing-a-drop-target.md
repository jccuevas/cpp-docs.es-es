---
title: "Arrastrar y colocar: Implementar un destino de colocaci&#243;n | Microsoft Docs"
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
  - "arrastrar y colocar, destino de colocación"
  - "funciones OLE de arrastrar y colocar, destino de colocación"
  - "funciones OLE de arrastrar y colocar, implementar destinos de colocación"
ms.assetid: 0689f1ec-5326-4008-b226-4b373c881358
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Arrastrar y colocar: Implementar un destino de colocaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe cómo crear la aplicación un destino.  Implementando un destino toma ligeramente más trabajo que implementando un origen de colocación, pero sigue siendo relativamente simple.  Estas técnicas también se aplica a las aplicaciones de no OLE.  
  
#### Para implementar un destino  
  
1.  Agregue una variable miembro a cada vista de la aplicación que desea ser un destino.  Esta variable miembro debe ser de `COleDropTarget` tipo o una clase derivada de ella.  
  
2.  De la función de clase de vista que controla el mensaje de `WM_CREATE` \(normalmente `OnCreate`\), llame a la función miembro de `Register` de la nueva variable miembro.  `Revoke` se llamará automáticamente automáticamente cuando se destruye la vista.  
  
3.  Reemplazar las funciones siguientes.  Si desea que el mismo comportamiento en la aplicación, reemplace estas funciones en la clase de vista.  Si desea modificar el comportamiento en casos aisladas o para desearlo para habilitar la interrupción en las ventanas no de`CView` , reemplace estas funciones en `COleDropTarget`\- clase derivada.  
  
    |Invalidación|Para permitir|  
    |------------------|-------------------|  
    |`OnDragEnter`|Operaciones de entrega mostrado en la ventana.  Llamado cuando el cursor primero entra en la ventana.|  
    |`OnDragLeave`|Comportamiento especial cuando la operación de arrastre sale de la ventana especificada.|  
    |`OnDragOver`|Operaciones de entrega mostrado en la ventana.  Llamado cuando el cursor se arrastra a través de la ventana.|  
    |`OnDrop`|El control de los datos que son descompuestos en la ventana especificada.|  
    |`OnScrollBy`|Comportamiento especial para cuando el desplazamiento es necesario en la ventana de destino.|  
  
 Vea el archivo de MAINVIEW.CPP que forma parte del ejemplo OLE [OCLIENT](../top/visual-cpp-samples.md) MFC para un ejemplo de cómo estas funciones trabajan juntos.  
  
 Para obtener más información, vea:  
  
-   [Implementar un origen de colocación](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [La creación y objetos de datos de OLE y orígenes de datos de Destruir](../mfc/data-objects-and-data-sources-creation-and-destruction.md)  
  
-   [Objetos de datos y orígenes de datos de OLE de manipulación](../mfc/data-objects-and-data-sources-manipulation.md)  
  
## Vea también  
 [Arrastrar y colocar \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDropTarget Class](../mfc/reference/coledroptarget-class.md)