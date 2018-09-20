---
title: OLE arrastrar y colocar y transferencia de datos clases | Microsoft Docs
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
ms.openlocfilehash: a4b5d694d0081fbe2d852884c4a379e962c22f2a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444143"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Clases de arrastrar y colocar y de transferencia de datos OLE

Estas clases se utilizan en las transferencias de datos OLE. Permite a transferirse entre aplicaciones mediante el Portapapeles o mediante arrastrar y colocar los datos.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Controla la operación de arrastrar y colocar de principio a fin. Esta clase determina cuando se inicia la operación de arrastrar y cuando termina. También se muestra la información del cursor durante la operación de arrastrar y colocar.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Se usa cuando una aplicación proporciona datos para una transferencia de datos. `COleDataSource` podría verse como un objeto de Portapapeles orientada a objetos.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Representa el destino de una operación de arrastrar y colocar. Un `COleDropTarget` objeto corresponde a una ventana en pantalla. Determina si se debe aceptar los datos colocan en él e implementa la operación de colocar real.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Usar como el lado receptor `COleDataSource`. `COleDataObject` objetos proporcionan acceso a los datos almacenados por una `COleDataSource` objeto.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

