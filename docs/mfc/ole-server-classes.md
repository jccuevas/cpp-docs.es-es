---
title: Clases de servidor OLE
ms.date: 11/04/2016
f1_keywords:
- vc.classes.ole
helpviewer_keywords:
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
ms.openlocfilehash: 610a69204e5cb66f2129351ab2a04bb0915a1b4c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451693"
---
# <a name="ole-server-classes"></a>Clases de servidor OLE

Estas clases se utilizan en aplicaciones de servidor. Documentos de servidor se derivan `COleServerDoc` en lugar de desde `CDocument`. Tenga en cuenta que dado que `COleServerDoc` se deriva de `COleLinkingDoc`, documentos de servidor también pueden ser contenedores que admiten la vinculación.

La `COleServerItem` clase representa un documento o una parte de un documento que se puede incrustar en otro documento o vinculado a.

`COleIPFrameWnd` y `COleResizeBar` admite edición en contexto mientras el objeto está en un contenedor, y `COleTemplateServer` admite la creación de pares de documento/vista por lo que se pueden editar los objetos OLE de otras aplicaciones.

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Se usa como clase base para las clases de documento de la aplicación de servidor. `COleServerDoc` los objetos proporcionan la mayor parte de la compatibilidad de servidor a través de las interacciones con `COleServerItem` objetos. Proporcionan la funcionalidad de edición visual con la arquitectura documento/vista de la biblioteca de clases.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Resumen de la clase base de `COleClientItem` y `COleServerItem`. Objetos de clases que derivan `CDocItem` representan elementos de documentos.

[COleServerItem](../mfc/reference/coleserveritem-class.md)<br/>
Utilizado para representar la interfaz OLE a `COleServerDoc` elementos. Normalmente, hay un `COleServerDoc` objeto, que representa la parte de un documento incrustada. En los servidores que admiten vínculos a elementos de documentos, puede haber muchos `COleServerItem` objetos, cada uno de los cuales representa un vínculo a una parte del documento.

[COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)<br/>
Proporciona la ventana de marco para obtener una vista cuando se está editando un documento de servidor en su lugar.

[COleResizeBar](../mfc/reference/coleresizebar-class.md)<br/>
Proporciona la interfaz de usuario estándar para dar nuevo tamaño en contexto. Objetos de esta clase siempre se usan junto con `COleIPFrameWnd` objetos.

[COleTemplateServer](../mfc/reference/coletemplateserver-class.md)<br/>
Se usa para crear documentos con la arquitectura documento/vista de .NET framework. Un `COleTemplateServer` objeto delega la mayor parte de su trabajo a un asociado `CDocTemplate` objeto.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Una excepción resultante de un error en el procesamiento de OLE. Esta clase se utiliza por contenedores y servidores.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)

