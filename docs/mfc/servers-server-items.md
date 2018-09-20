---
title: 'Servidores: Elementos de servidor | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72f8de75607921edda62aec9baec424066431d61
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46438865"
---
# <a name="servers-server-items"></a>Servidores: Elementos de servidor

Cuando un contenedor inicia un servidor para que un usuario puede editar un elemento OLE incrustado o vinculado, la aplicación de servidor crea un "elemento de servidor". El elemento del servidor, que es un objeto de una clase derivada de `COleServerItem`, proporciona una interfaz entre el documento del servidor y la aplicación contenedora.

La `COleServerItem` clase define varias funciones miembro reemplazables que se denominan OLE, normalmente en respuesta a las solicitudes desde el contenedor. Los elementos del servidor pueden representar una parte del documento de servidor o todo el documento. Cuando un elemento OLE se incrusta en el documento contenedor, el elemento de servidor representa el documento de todo el servidor. Cuando se vincula el elemento OLE, el elemento del servidor puede representar una parte del documento de servidor o el documento completo, dependiendo de si el vínculo es una parte o la totalidad.

En el [HIERSVR](../visual-cpp-samples.md) muestrear, por ejemplo, la clase de elemento de servidor, `CServerItem`, tiene un miembro que es un puntero a un objeto de la clase `CServerNode`. La `CServerNode` objeto es un nodo de documento de la aplicación HIERSVR, que es un árbol. Cuando el `CServerNode` objeto es el nodo raíz, el `CServerItem` objeto representa el documento completo. Cuando el `CServerNode` objeto es un nodo secundario, el `CServerItem` objeto representa una parte del documento. Vea el ejemplo OLE de MFC [HIERSVR](../visual-cpp-samples.md) para obtener un ejemplo de esta interacción.

##  <a name="_core_implementing_server_items"></a> Implementar elementos de servidor

Si usa el Asistente para aplicaciones para generar código de "inicio" para la aplicación, todo lo que debe hacer para incluir los elementos del servidor en el código de inicio es elegir una de las opciones de servidor desde la página Opciones OLE. Si va a agregar los elementos del servidor a una aplicación existente, realice los pasos siguientes:

#### <a name="to-implement-a-server-item"></a>Para implementar un elemento del servidor

1. Derivar una clase de `COleServerItem`.

1. En la clase derivada, invalide el `OnDraw` función miembro.

     Las llamadas de framework `OnDraw` para representar el elemento OLE en un metarchivo. La aplicación contenedora usa este metarchivo para presentar el elemento. Clase de vista de la aplicación también tiene un `OnDraw` función miembro, que se usa para representar el elemento cuando la aplicación de servidor está activa.

1. Implemente un reemplazo de `OnGetEmbeddedItem` para la clase de documento de servidor. Para obtener más información, consulte el artículo [servidores: implementar documentos de servidor](../mfc/servers-implementing-server-documents.md) y el ejemplo OLE de MFC [HIERSVR](../visual-cpp-samples.md).

1. Implementar la clase de elemento de servidor `OnGetExtent` función miembro. El marco de trabajo llama a esta función para recuperar el tamaño del elemento. La implementación predeterminada no hace nada.

##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Una sugerencia para la arquitectura de elemento de servidor

Como se indicó en [implementar elementos de servidor](#_core_implementing_server_items), las aplicaciones de servidor deben ser capaces de representar los elementos en la vista del servidor y en un metarchivo utilizado por la aplicación de contenedor. En arquitectura de aplicaciones de la biblioteca Microsoft Foundation Class, la clase de vista `OnDraw` función miembro representa el elemento cuando se está editando (consulte [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw) en el *referencia de biblioteca de clases* ). El elemento de servidor `OnDraw` representa el elemento en un metarchivo en todos los demás casos (consulte [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Puede evitar la duplicación de código escribiendo funciones auxiliares en la clase de documento de servidor y llamarlos desde el `OnDraw` funciones en las clases de vista y el elemento de servidor. El ejemplo OLE de MFC [HIERSVR](../visual-cpp-samples.md) usa esta estrategia: las funciones `CServerView::OnDraw` y `CServerItem::OnDraw` llaman a `CServerDoc::DrawTree` para representar el elemento.

La vista y el elemento tienen `OnDraw` funciones miembro, puesto que se dibujan en diferentes condiciones. La vista debe tener en cuenta factores tales como Zoom, tamaño de la selección y extensión, recorte y elementos de interfaz de usuario, como las barras de desplazamiento. Por otro lado, el elemento del servidor, siempre dibuja todo el objeto OLE.

Para obtener más información, consulte [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), y [COleServerDoc:: OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)en el *referencia de la biblioteca de clases*.

## <a name="see-also"></a>Vea también

[Servidores](../mfc/servers.md)

