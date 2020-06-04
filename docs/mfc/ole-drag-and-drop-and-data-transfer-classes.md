---
title: Clases de arrastrar y colocar y de transferencia de datos OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- OLE drag and drop [MFC], and data transfer classes
- drag and drop [MFC], classes
- data transfer [MFC], OLE
- data transfer classes [MFC]
ms.assetid: c8ab2825-ed69-4b88-8ae6-f368b94726b8
ms.openlocfilehash: 7e01b6d5a7d14e0af4ca760e6e601e91359c8ab1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447616"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Clases de arrastrar y colocar y de transferencia de datos OLE

Estas clases se utilizan en las transferencias de datos OLE. Permiten la transferencia de datos entre aplicaciones mediante el uso del portapapeles o a través de la función de arrastrar y colocar.

[COleDropSource](../mfc/reference/coledropsource-class.md)<br/>
Controla la operación de arrastrar y colocar de principio a fin. Esta clase determina cuándo se inicia la operación de arrastre y cuándo finaliza. También se muestran los comentarios del cursor durante la operación de arrastrar y colocar.

[COleDataSource](../mfc/reference/coledatasource-class.md)<br/>
Se utiliza cuando una aplicación proporciona datos para una transferencia de datos. `COleDataSource` podría verse como un objeto Clipboard orientado a objetos.

[COleDropTarget](../mfc/reference/coledroptarget-class.md)<br/>
Representa el destino de una operación de arrastrar y colocar. Un objeto `COleDropTarget` corresponde a una ventana en la pantalla. Determina si se debe aceptar cualquier dato colocado en él e implementa la operación de colocación real.

[COleDataObject](../mfc/reference/coledataobject-class.md)<br/>
Se utiliza como receptor para `COleDataSource`. `COleDataObject` objetos proporcionan acceso a los datos almacenados por un objeto `COleDataSource`.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
