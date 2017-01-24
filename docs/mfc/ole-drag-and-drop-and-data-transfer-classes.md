---
title: "Clases de arrastrar y colocar y de transferencia de datos OLE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.classes.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX (clases) [C++]"
  - "transferencia de datos [C++], OLE"
  - "clases de transferencia de datos [C++]"
  - "arrastrar y colocar [C++], clases"
  - "arrastrar y colocar OLE [C++], y clases de transferencia de datos"
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de arrastrar y colocar y de transferencia de datos OLE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estas clases se utilizan en las transferencias de datos VIEJAS.  Permiten que los datos se transfieren entre las aplicaciones utilizando el portapapeles o con arrastrar y colocar.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 Controla la operación de arrastrar y colocar de principio a fin.  Esta clase determina cuando la operación de arrastre inicia y cuando finaliza.  También muestra la información del cursor durante la operación de arrastrar y colocar.  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 Se utiliza cuando una aplicación proporciona los datos para una transferencia de datos.  `COleDataSource` se puede ver como objeto orientado a objetos del portapapeles.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 Representa el destino de una operación de arrastrar y colocar.  Un objeto de `COleDropTarget` corresponde a una ventana en la pantalla.  Determina si aceptar los datos quitado sobre él se implementa la operación real de entrega.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 Se utiliza como el lado receptor a `COleDataSource`.  los objetos de`COleDataObject` proporcionan acceso a los datos almacenados en un objeto de `COleDataSource` .  
  
## Vea también  
 [Información general de clases](../mfc/class-library-overview.md)