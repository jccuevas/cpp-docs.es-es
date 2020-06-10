---
title: Clases de servidor OLE
ms.date: 11/04/2016
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 06f5cf0985756506e42c7ad9fde24641b5a0ce93
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619863"
---
# <a name="ole-server-classes"></a>Clases de servidor OLE

Estas clases se usan en las aplicaciones de servidor. Los documentos de servidor se derivan de `COleServerDoc` y no de `CDocument` . Tenga en cuenta que, dado que `COleServerDoc` se deriva de `COleLinkingDoc` , los documentos de servidor también pueden ser contenedores que admiten la vinculación.

La `COleServerItem` clase representa un documento o parte de un documento que se puede incrustar en otro documento o vincular a.

`COleIPFrameWnd`y `COleResizeBar` admiten la edición en contexto mientras el objeto está en un contenedor y `COleTemplateServer` admite la creación de pares documento/vista, por lo que se pueden editar objetos OLE de otras aplicaciones.

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Se utiliza como clase base para las clases de documento de aplicación de servidor. `COleServerDoc`los objetos proporcionan la mayor compatibilidad de servidor a través de las interacciones con los `COleServerItem` objetos. La capacidad de edición visual se proporciona mediante la arquitectura documento/vista de la biblioteca de clases.

[CDocItem](reference/cdocitem-class.md)<br/>
Clase base abstracta de `COleClientItem` y `COleServerItem` . Los objetos de clases derivadas de `CDocItem` representan partes de documentos.

[COleServerItem](reference/coleserveritem-class.md)<br/>
Se utiliza para representar la interfaz OLE para `COleServerDoc` los elementos. Normalmente hay un `COleServerDoc` objeto, que representa la parte incrustada de un documento. En los servidores que admiten vínculos a partes de documentos, puede haber muchos `COleServerItem` objetos, cada uno de los cuales representa un vínculo a una parte del documento.

[COleIPFrameWnd](reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para una vista cuando se está editando un documento de servidor en su lugar.

[COleResizeBar](reference/coleresizebar-class.md)<br/>
Proporciona la interfaz de usuario estándar para el cambio de tamaño en contexto. Los objetos de esta clase siempre se usan junto con los `COleIPFrameWnd` objetos.

[COleTemplateServer](reference/coletemplateserver-class.md)<br/>
Se usa para crear documentos con la arquitectura documento/vista del marco de trabajo. Un `COleTemplateServer` objeto delega la mayor parte de su trabajo en un `CDocTemplate` objeto asociado.

[COleException](reference/coleexception-class.md)<br/>
Excepción generada por un error en el procesamiento de OLE. Esta clase la usan los contenedores y los servidores.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
