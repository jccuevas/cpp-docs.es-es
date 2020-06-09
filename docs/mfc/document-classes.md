---
title: Clases de documento
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
ms.openlocfilehash: 012d107d7bcc630c4bc02a9dc697172080787eac
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615802"
---
# <a name="document-classes"></a>Clases de documento

Los objetos de clase de documento, creados por objetos de plantilla de documento, administran los datos de la aplicación. Derivará una clase para los documentos de una de estas clases.

Los objetos de clase de documento interactúan con objetos de vista. Los objetos de vista representan el área cliente de una ventana, muestran los datos de un documento y permiten a los usuarios interactuar con él. Los documentos y las vistas se crean mediante un objeto de plantilla de documento.

[CDocument](reference/cdocument-class.md)<br/>
La clase base para los documentos específicos de la aplicación. Derive la clase o clases de documento de `CDocument` .

[COleDocument](reference/coledocument-class.md)<br/>
Se usa para la implementación de documentos compuestos, así como la compatibilidad con contenedores básicos. Actúa como contenedor para las clases derivadas de [CDocItem](reference/cdocitem-class.md). Esta clase se puede usar como clase base para los documentos de contenedor y es la clase base para `COleServerDoc` .

[COleLinkingDoc](reference/colelinkingdoc-class.md)<br/>
Una clase derivada de `COleDocument` que proporciona la infraestructura para la vinculación. Debe derivar las clases de documento de las aplicaciones de contenedor de esta clase en lugar de `COleDocument` si desea que admitan vínculos a objetos incrustados.

[CRichEditDoc](reference/cricheditdoc-class.md)<br/>
Mantiene la lista de elementos de cliente OLE que se encuentran en el control Rich Edit. Se usa con [CRichEditView](reference/cricheditview-class.md) y [CRichEditCntrItem](reference/cricheditcntritem-class.md).

[COleServerDoc](reference/coleserverdoc-class.md)<br/>
Se utiliza como clase base para las clases de documento de aplicación de servidor. `COleServerDoc`los objetos proporcionan la mayor compatibilidad de servidor a través de las interacciones con objetos [COleServerItem](reference/coleserveritem-class.md) . La capacidad de edición visual se proporciona mediante la arquitectura documento/vista de la biblioteca de clases.

[CHtmlEditDoc](reference/chtmleditdoc-class.md)<br/>
Proporciona, con [CHtmlEditView](reference/chtmleditview-class.md), la funcionalidad de la plataforma de edición HTML de WebBrowser en el contexto de la arquitectura de vista-documento de MFC.

## <a name="related-classes"></a>Clases relacionadas

Los objetos de clase de documento pueden ser persistentes; es decir, pueden escribir su estado en un medio de almacenamiento y volver a leerlo. MFC proporciona la `CArchive` clase para facilitar la transferencia de datos del documento a un medio de almacenamiento.

[CArchive](reference/carchive-class.md)<br/>
Coopera con un objeto [CFile](reference/cfile-class.md) para implementar el almacenamiento persistente para los objetos a través de la serialización (vea [CObject:: Serialize](reference/cobject-class.md#serialize)).

Los documentos también pueden contener objetos OLE. `CDocItem`es la clase base de los elementos de servidor y de cliente.

[CDocItem](reference/cdocitem-class.md)<br/>
Clase base abstracta de [COleClientItem](reference/coleclientitem-class.md) y [COleServerItem](reference/coleserveritem-class.md). Los objetos de clases derivadas de `CDocItem` representan partes de documentos.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
