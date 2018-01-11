---
title: OLE de arrastrar y colocar y datos de clases de transferencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.classes.ole
dev_langs: C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0e8c5a54184bcf6450bf39b39a6b90d7865c09d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Clases de arrastrar y colocar y de transferencia de datos OLE
Estas clases se utilizan en las transferencias de datos OLE. Permite que los datos se transfieren entre las aplicaciones mediante el Portapapeles o mediante arrastrar y colocar.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 Controla la operación de arrastrar y colocar de principio a fin. Esta clase determina cuando se inicia la operación de arrastre y cuando termina. También se muestra la información del cursor durante la operación de arrastrar y colocar.  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 Se utiliza cuando una aplicación proporciona datos para una transferencia de datos. `COleDataSource`podría interpretarse como un objeto de Portapapeles orientada a objetos.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 Representa el destino de una operación de arrastrar y colocar. Un `COleDropTarget` objeto corresponde a una ventana en la pantalla. Determina si se debe aceptar los datos coloquen en él e implementa la operación de eliminación real.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 Usar como el lado receptor `COleDataSource`. `COleDataObject`objetos proporcionan acceso a los datos almacenados por una `COleDataSource` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

