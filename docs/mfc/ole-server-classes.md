---
title: Clases de servidor OLE | Documentos de Microsoft
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
- OLE server applications [MFC], server classes
- OLE server documents
- COM components, classes [MFC]
- component classes [MFC]
ms.assetid: 8e9b67a2-c0ff-479c-a8d6-19b36c5e6fc6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e9d0c75325c62a92f65c56f2c76350bf752228fd
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932226"
---
# <a name="ole-server-classes"></a>Clases de servidor OLE
Estas clases se utilizan en aplicaciones de servidor. Documentos de servidor se derivan `COleServerDoc` en lugar de en `CDocument`. Tenga en cuenta que, dado que `COleServerDoc` se deriva de `COleLinkingDoc`, documentos de servidor también pueden ser contenedores que admiten la vinculación.  
  
 La `COleServerItem` clase representa un documento o una parte de un documento que se pueden incrustar en otro documento o vinculado.  
  
 `COleIPFrameWnd` y `COleResizeBar` admite la edición en contexto mientras el objeto está en un contenedor, y `COleTemplateServer` admite la creación de pares de documento/vista por lo que se pueden editar los objetos OLE de otras aplicaciones.  
  
 [COleServerDoc](../mfc/reference/coleserverdoc-class.md)  
 Se utiliza como la clase base para las clases de documento de la aplicación de servidor. `COleServerDoc` objetos proporcionan la mayor parte de la compatibilidad de servidor a través de las interacciones con `COleServerItem` objetos. Capacidad de edición visual se proporciona mediante la arquitectura documento/vista de la biblioteca de clases.  
  
 [CDocItem](../mfc/reference/cdocitem-class.md)  
 Abstracta de la clase base de `COleClientItem` y `COleServerItem`. Objetos de clases derivadas de `CDocItem` representan partes de documentos.  
  
 [COleServerItem](../mfc/reference/coleserveritem-class.md)  
 Utilizado para representar la interfaz OLE a `COleServerDoc` elementos. Normalmente hay un `COleServerDoc` objeto, que representa la parte de un documento incrustada. En servidores que admiten vínculos a elementos de documentos, puede haber muchos `COleServerItem` objetos, cada uno de los cuales representa un vínculo a una parte del documento.  
  
 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)  
 Proporciona la ventana de marco para obtener una vista cuando se está editando un documento del servidor en su lugar.  
  
 [COleResizeBar](../mfc/reference/coleresizebar-class.md)  
 Proporciona la interfaz de usuario estándar para dar nuevo tamaño en contexto. Objetos de esta clase siempre se usan junto con `COleIPFrameWnd` objetos.  
  
 [COleTemplateServer](../mfc/reference/coletemplateserver-class.md)  
 Se usa para crear documentos con la arquitectura de documento/vista del marco de trabajo. A `COleTemplateServer` objeto delega la mayor parte de su trabajo a un asociado `CDocTemplate` objeto.  
  
 [COleException](../mfc/reference/coleexception-class.md)  
 Una excepción resultante de un error en el procesamiento de OLE. Esta clase se utiliza por contenedores y servidores.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

