---
title: Clases de contenedor OLE
ms.date: 11/04/2016
helpviewer_keywords:
- ActiveX classes [MFC]
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
ms.openlocfilehash: 61db5310637d13da2d2cc183f12f8f62aa60e328
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447654"
---
# <a name="ole-container-classes"></a>Clases de contenedor OLE

Estas clases las usan las aplicaciones de contenedor. Tanto `COleLinkingDoc` como `COleDocument` administran colecciones de objetos `COleClientItem`. En lugar de derivar la clase de documento de `CDocument`, la derivará de `COleLinkingDoc` o `COleDocument`, en función de si desea admitir vínculos a los objetos incrustados en el documento.

Use un objeto `COleClientItem` para representar cada elemento OLE del documento que está incrustado desde otro documento o es un vínculo a otro documento.

[COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)<br/>
Admite la contención de documentos activos.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Se usa para la implementación de documentos compuestos, así como la compatibilidad con contenedores básicos. Actúa como contenedor para las clases derivadas de `CDocItem`. Esta clase se puede usar como clase base para los documentos de contenedor y es la clase base para `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Clase derivada de `COleDocument` que proporciona la infraestructura para la vinculación. Debe derivar las clases de documento de las aplicaciones contenedoras de esta clase en lugar de `COleDocument` si desea que admitan vínculos a objetos incrustados.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Mantiene la lista de elementos de cliente OLE que se encuentran en el control Rich Edit. Se usa con [CRichEditView](../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Clase base abstracta de `COleClientItem` y `COleServerItem`. Los objetos de clases derivadas de `CDocItem` representan partes de documentos.

[COleClientItem](../mfc/reference/coleclientitem-class.md)<br/>
Una clase de elemento de cliente que representa el lado del cliente de la conexión a un elemento OLE incrustado o vinculado. Derive los elementos de cliente de esta clase.

[CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)<br/>
Proporciona acceso del lado cliente a un elemento OLE almacenado en un control Rich Edit cuando se usa con `CRichEditView` y `CRichEditDoc`.

[COleException](../mfc/reference/coleexception-class.md)<br/>
Excepción generada por un error en el procesamiento de OLE. Esta clase la usan los contenedores y los servidores.

## <a name="see-also"></a>Consulte también

[Información general sobre clases](../mfc/class-library-overview.md)
