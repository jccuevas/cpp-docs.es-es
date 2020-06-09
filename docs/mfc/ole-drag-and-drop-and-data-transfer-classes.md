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
ms.openlocfilehash: 530b1772dfb623689facd5b14eebe9ed1eacd4fd
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624140"
---
# <a name="ole-drag-and-drop-and-data-transfer-classes"></a>Clases de arrastrar y colocar y de transferencia de datos OLE

Estas clases se utilizan en las transferencias de datos OLE. Permiten la transferencia de datos entre aplicaciones mediante el uso del portapapeles o a través de la función de arrastrar y colocar.

[COleDropSource](reference/coledropsource-class.md)<br/>
Controla la operación de arrastrar y colocar de principio a fin. Esta clase determina cuándo se inicia la operación de arrastre y cuándo finaliza. También se muestran los comentarios del cursor durante la operación de arrastrar y colocar.

[COleDataSource](reference/coledatasource-class.md)<br/>
Se utiliza cuando una aplicación proporciona datos para una transferencia de datos. `COleDataSource`se puede ver como un objeto Clipboard orientado a objetos.

[COleDropTarget](reference/coledroptarget-class.md)<br/>
Representa el destino de una operación de arrastrar y colocar. Un `COleDropTarget` objeto corresponde a una ventana en la pantalla. Determina si se debe aceptar cualquier dato colocado en él e implementa la operación de colocación real.

[COleDataObject](reference/coledataobject-class.md)<br/>
Se utiliza como receptor para `COleDataSource` . `COleDataObject`los objetos proporcionan acceso a los datos almacenados por un `COleDataSource` objeto.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
