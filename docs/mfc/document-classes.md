---
title: Clases de documento
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: a7034a99bfefe8f4c11cdf8f99dc4b0c31fac10a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57289720"
---
# <a name="document-classes"></a>Clases de documento

Objetos de clase de documento, creados los objetos de plantilla de documento, administran los datos de la aplicación. Derivará una clase para los documentos de una de estas clases.

Objetos de clase de documento interactúan con objetos de vista. Ver objetos representan el área cliente de una ventana, mostrar los datos de un documento y permiten a los usuarios interactuar con él. Documentos y vistas se crean mediante un objeto de plantilla de documento.

[CDocument](../mfc/reference/cdocument-class.md)<br/>
La clase base para los documentos específicos de la aplicación. Derive la clase de documento o clases de `CDocument`.

[COleDocument](../mfc/reference/coledocument-class.md)<br/>
Se utiliza para la implementación de documento compuesto, así como compatibilidad con contenedores básica. Actúa como un contenedor para las clases derivadas de [CDocItem](../mfc/reference/cdocitem-class.md). Esta clase puede utilizarse como clase base para el contenedor de documentos y es la clase base para `COleServerDoc`.

[COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)<br/>
Una clase derivada de `COleDocument` que proporciona la infraestructura para la vinculación. Debe derivar las clases de documento para sus aplicaciones de contenedor de esta clase en lugar de desde `COleDocument` si desea admitir vínculos a objetos incrustados.

[CRichEditDoc](../mfc/reference/cricheditdoc-class.md)<br/>
Mantiene la lista de elementos de cliente OLE que se encuentran en el control de edición enriquecida. Puede usar con [CRichEditView](../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).

[COleServerDoc](../mfc/reference/coleserverdoc-class.md)<br/>
Se usa como clase base para las clases de documento de la aplicación de servidor. `COleServerDoc` los objetos proporcionan la mayor parte de la compatibilidad de servidor a través de las interacciones con [COleServerItem](../mfc/reference/coleserveritem-class.md) objetos. Proporcionan la funcionalidad de edición visual con la arquitectura documento/vista de la biblioteca de clases.

[CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)<br/>
Proporciona, con [CHtmlEditView](../mfc/reference/chtmleditview-class.md), la funcionalidad de la plataforma de edición WebBrowser HTML dentro del contexto de la arquitectura de vista-documento MFC.

## <a name="related-classes"></a>Clases relacionadas

Objetos de clase de documento pueden ser persistentes; en otras palabras, puede escribir su estado en un medio de almacenamiento y leerlos. MFC proporciona la `CArchive` clase para facilitar la transferencia de los datos del documento a un medio de almacenamiento.

[CArchive](../mfc/reference/carchive-class.md)<br/>
Coopera con un [CFile](../mfc/reference/cfile-class.md) objeto para implementar el almacenamiento persistente para los objetos mediante la serialización (vea [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)).

Documentos también pueden contener objetos OLE. `CDocItem` es la clase base de los elementos de cliente y servidor.

[CDocItem](../mfc/reference/cdocitem-class.md)<br/>
Resumen de la clase base de [COleClientItem](../mfc/reference/coleclientitem-class.md) y [COleServerItem](../mfc/reference/coleserveritem-class.md). Objetos de clases que derivan `CDocItem` representan elementos de documentos.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
