---
title: Clases de contenedor OLE | Documentos de Microsoft
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
- container classes [MFC]
- OLE classes [MFC]
- visual editing [MFC], classes
- OLE [MFC], classes
- containers [MFC], OLE container applications
ms.assetid: 1e27e1ab-4c22-41eb-8547-6915c72668ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6f8214b2f40926cc4ab1471dce99ce5215362011
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930495"
---
# <a name="ole-container-classes"></a>Clases de contenedor OLE
Estas clases se utilizan las aplicaciones de contenedor. Ambos `COleLinkingDoc` y `COleDocument` administrar colecciones de `COleClientItem` objetos. En lugar de derivar la clase de documento de `CDocument`, podrá derivar desde `COleLinkingDoc` o `COleDocument`, dependiendo de si desea soporte técnico para obtener vínculos a objetos incrustados en el documento.  
  
 Use un `COleClientItem` objeto para representar cada elemento OLE en el documento que está incrustado en otro documento o un vínculo a otro documento.  
  
 [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)  
 Admite la contención de documentos activos.  
  
 [COleDocument](../mfc/reference/coledocument-class.md)  
 Se utiliza para la implementación de documento compuesto, así como compatibilidad con el contenedor básico. Actúa como un contenedor para las clases derivadas de `CDocItem`. Esta clase puede usarse como clase base para el contenedor de documentos y es la clase base para `COleServerDoc`.  
  
 [COleLinkingDoc](../mfc/reference/colelinkingdoc-class.md)  
 Una clase derivada de `COleDocument` que proporciona la infraestructura para crear un vínculo. Debe derivar las clases de documento para sus aplicaciones de contenedor de esta clase en lugar de desde `COleDocument` si desea admitir vínculos a objetos incrustados.  
  
 [CRichEditDoc](../mfc/reference/cricheditdoc-class.md)  
 Mantiene la lista de elementos de cliente OLE que se encuentran en el control de edición enriquecida. Usar con [CRichEditView](../mfc/reference/cricheditview-class.md) y [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md).  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstracta de la clase base de `COleClientItem` y `COleServerItem`. Objetos de clases derivadas de `CDocItem` representan partes de documentos.  
  
 [COleClientItem](../mfc/reference/coleclientitem-class.md)  
 Una clase de elemento de cliente que representa el lado del cliente de la conexión a un elemento OLE incrustado o vinculado. Los elementos de cliente se derivan de esta clase.  
  
 [CRichEditCntrItem](../mfc/reference/cricheditcntritem-class.md)  
 Proporciona acceso de cliente a un elemento almacenado en un control rich edit cuando se usa con OLE `CRichEditView` y `CRichEditDoc`.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Una excepción resultante de un error en el procesamiento de OLE. Esta clase se utiliza por contenedores y servidores.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

