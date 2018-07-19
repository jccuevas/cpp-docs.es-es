---
title: OLE de arrastrar y colocar y datos de clases de transferencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.ole
dev_langs:
- C++
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d55d6d171f490631afe17a605f50607fb55f070b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347047"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Clases de arrastrar y colocar y de transferencia de datos OLE
Estas clases se utilizan en las transferencias de datos OLE. Permite que los datos se transfieren entre las aplicaciones mediante el Portapapeles o mediante arrastrar y colocar.  
  
 [COleDropSource](../mfc/reference/coledropsource-class.md)  
 Controla la operación de arrastrar y colocar de principio a fin. Esta clase determina cuando se inicia la operación de arrastre y cuando termina. También se muestra la información del cursor durante la operación de arrastrar y colocar.  
  
 [COleDataSource](../mfc/reference/coledatasource-class.md)  
 Se utiliza cuando una aplicación proporciona datos para una transferencia de datos. `COleDataSource` podría interpretarse como un objeto de Portapapeles orientada a objetos.  
  
 [COleDropTarget](../mfc/reference/coledroptarget-class.md)  
 Representa el destino de una operación de arrastrar y colocar. Un `COleDropTarget` objeto corresponde a una ventana en la pantalla. Determina si se debe aceptar los datos coloquen en él e implementa la operación de eliminación real.  
  
 [COleDataObject](../mfc/reference/coledataobject-class.md)  
 Usar como el lado receptor `COleDataSource`. `COleDataObject` objetos proporcionan acceso a los datos almacenados por una `COleDataSource` objeto.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

