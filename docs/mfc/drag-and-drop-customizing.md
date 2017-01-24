---
title: "Arrastrar y colocar: Personalizaci&#243;n | Microsoft Docs"
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
  - "arrastrar y colocar, llamar a DoDragDrop"
  - "arrastrar y colocar, COleDataSource (objeto)"
  - "arrastrar y colocar, personalizar el comportamiento"
  - "arrastrar y colocar, implementar en aplicaciones no OLE"
  - "funciones OLE de arrastrar y colocar, personalizar el comportamiento"
ms.assetid: 03369d3e-46bf-4140-b58c-d0c9657cf38a
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Arrastrar y colocar: Personalizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La implementación predeterminada de la característica de arrastrar y colocar es suficiente para la mayoría de las aplicaciones.  Sin embargo, algunas aplicaciones pueden requerir que este comportamiento estándar está cambiado.  En este artículo se explica los pasos necesarios para cambiar estos valores predeterminados.  Además, puede utilizar esta técnica para establecer las aplicaciones que no admiten documentos compuestos como orígenes de posición.  
  
 Si está personalizando el comportamiento estándar de arrastrar y colocar de OLE, o tiene una aplicación de no OLE, debe crear un objeto de `COleDataSource` para contener datos.  Cuando el usuario inicia una operación de arrastrar y colocar, el código debe llamar a la función de `DoDragDrop` de este objeto en lugar de otras clases que las operaciones de arrastrar y colocar admiten.  
  
 Opcionalmente, puede crear un objeto de `COleDropSource` para controlar el destino y para invalidar algunas de sus funciones según el tipo de comportamiento que desea cambiar.  Este objeto de origen de posición se pasa a `COleDataSource::DoDragDrop` para cambiar el comportamiento predeterminado de estas funciones.  Estas opciones diferentes permiten mucha flexibilidad para admite operaciones de arrastrar y colocar en la aplicación.  Para obtener más información sobre los orígenes de datos, vea el artículo [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md).  
  
 Puede invalidar las siguientes funciones para personalizar las operaciones de arrastrar y colocar:  
  
|Invalidación|Para personalizar|  
|------------------|-----------------------|  
|`OnBeginDrag`|Cómo arrastrar se inicia después de llamar a `DoDragDrop`.|  
|`GiveFeedback`|Comentarios visuales, como apariencia de cursor, para distintos resultados de entrega.|  
|`QueryContinueDrag`|La finalización de una operación de arrastrar y colocar.  Esta función permite comprobar los estados de la tecla modificadora durante la operación de arrastre.|  
  
## Vea también  
 [Arrastrar y colocar \(OLE\)](../mfc/drag-and-drop-ole.md)   
 [COleDropSource Class](../mfc/reference/coledropsource-class.md)   
 [COleDataSource Class](../mfc/reference/coledatasource-class.md)