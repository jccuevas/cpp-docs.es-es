---
title: Clases de documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.document
dev_langs:
- C++
helpviewer_keywords:
- document classes [MFC]
ms.assetid: 4bf19b02-0a4f-4319-b68e-cddcba2705cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 33068a96d8d0ca0a228012385da6437c455468e5
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928546"
---
# <a name="document-classes"></a>Clases de documento
Objetos de clase de documento, creados por objetos de plantilla de documento, administran los datos de la aplicación. Se deriva una clase de los documentos de una de estas clases.  
  
 Objetos de clase de documento interactúan con objetos de vista. Ver objetos representan el área de cliente de una ventana, mostrar datos de un documento y permiten a los usuarios interactuar con él. Documentos y vistas se crean un objeto de plantilla de documento.  
  
 [CDocument](../mfc/reference/cdocument-class.md)  
 La clase base para documentos específicos de la aplicación. Derive la clase de documento o clases de `CDocument`.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Se utiliza para la implementación de documento compuesto, así como compatibilidad con el contenedor básico. Actúa como un contenedor para las clases derivadas de [CDocItem](../mfc/reference/cdocitem-class.md). Esta clase puede usarse como clase base para el contenedor de documentos y es la clase base para `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Una clase derivada de `COleDocument` que proporciona la infraestructura para crear un vínculo. Debe derivar las clases de documento para sus aplicaciones de contenedor de esta clase en lugar de desde `COleDocument` si desea admitir vínculos a objetos incrustados.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Mantiene la lista de elementos de cliente OLE que se encuentran en el control de edición enriquecida. Usar con [CRichEditView](../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Se utiliza como la clase base para las clases de documento de la aplicación de servidor. `COleServerDoc` objetos proporcionan la mayor parte de la compatibilidad de servidor a través de las interacciones con [COleServerItem](../mfc/reference/coleserveritem-class.md) objetos. Capacidad de edición visual se proporciona mediante la arquitectura documento/vista de la biblioteca de clases.  
  
 [CHtmlEditDoc](../mfc/reference/chtmleditdoc-class.md)  
 Proporciona, con [CHtmlEditView](../mfc/reference/chtmleditview-class.md), la funcionalidad de la plataforma de edición HTML de WebBrowser en el contexto de la arquitectura de vista-documento MFC.  
  
## <a name="related-classes"></a>Clases relacionadas  
 Objetos de clase de documento pueden ser persistentes; en otras palabras, puede escribir su estado en un medio de almacenamiento y leerlos. MFC proporciona la `CArchive` clase para facilitar la transferencia de los datos del documento en un medio de almacenamiento.  
  
 [CArchive](../mfc/reference/carchive-class.md)  
 Coopera con un [CFile](../mfc/reference/cfile-class.md) objeto que se va a implementar el almacenamiento persistente para los objetos mediante la serialización (vea [CObject:: Serialize](../mfc/reference/cobject-class.md#serialize)).  
  
 Documentos también pueden contener objetos OLE. `CDocItem` es la clase base de los elementos de cliente y servidor.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstracta de la clase base de [COleClientItem](../mfc/reference/coleclientitem-class.md) y [COleServerItem](../mfc/reference/coleserveritem-class.md). Objetos de clases derivadas de `CDocItem` representan partes de documentos.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

