---
title: 'Servidores: Elementos de servidor'
ms.date: 11/04/2016
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
ms.openlocfilehash: 8ae24104a30a0b44e92b889006907911124310f7
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355109"
---
# <a name="servers-server-items"></a>Servidores: Elementos de servidor

Cuando un contenedor inicia un servidor para que un usuario pueda editar un elemento OLE incrustado o vinculado, la aplicación de servidor crea un "elemento de servidor." El elemento de servidor, que es un `COleServerItem`objeto de una clase derivada de , proporciona una interfaz entre el documento de servidor y la aplicación contenedora.

La `COleServerItem` clase define varias funciones miembro reemplazables a las que llama OLE, normalmente en respuesta a las solicitudes del contenedor. Los elementos de servidor pueden representar parte del documento de servidor o de todo el documento. Cuando se incrusta un elemento OLE en el documento contenedor, el elemento de servidor representa todo el documento de servidor. Cuando el elemento OLE está vinculado, el elemento de servidor puede representar una parte del documento de servidor o todo el documento, dependiendo de si el vínculo es a una parte o a la totalidad.

En el ejemplo [HIERSVR,](../overview/visual-cpp-samples.md) por ejemplo, `CServerItem`la clase server-item, , tiene un `CServerNode`miembro que es un puntero a un objeto de la clase . El `CServerNode` objeto es un nodo en el documento de la aplicación HIERSVR, que es un árbol. Cuando `CServerNode` el objeto es el `CServerItem` nodo raíz, el objeto representa todo el documento. Cuando `CServerNode` el objeto es un `CServerItem` nodo secundario, el objeto representa una parte del documento. Vea el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md) para obtener un ejemplo de esta interacción.

## <a name="implementing-server-items"></a><a name="_core_implementing_server_items"></a>Implementación de elementos de servidor

Si usa el asistente de aplicación para generar código de "inicio" para la aplicación, todo lo que tiene que hacer para incluir elementos de servidor en el código de inicio es elegir una de las opciones de servidor de la página Opciones OLE. Si va a agregar elementos de servidor a una aplicación existente, siga estos pasos:

#### <a name="to-implement-a-server-item"></a>Para implementar un elemento de servidor

1. Derivar una clase de `COleServerItem`.

1. En la clase derivada, `OnDraw` invalide la función miembro.

   El marco `OnDraw` de trabajo llama para representar el elemento OLE en un metarchivo. La aplicación contenedora utiliza este metarchivo para representar el elemento. La clase de vista de `OnDraw` la aplicación también tiene una función miembro, que se usa para representar el elemento cuando la aplicación de servidor está activa.

1. Implemente una `OnGetEmbeddedItem` invalidación de la clase de documento de servidor. Para obtener más información, vea el artículo [Servidores: implementación](../mfc/servers-implementing-server-documents.md) de documentos de servidor y el ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md).

1. Implemente la función miembro `OnGetExtent` de la clase de elemento de servidor. El marco de trabajo llama a esta función para recuperar el tamaño del elemento. La implementación predeterminada no hace nada.

## <a name="a-tip-for-server-item-architecture"></a><a name="_core_a_tip_for_server.2d.item_architecture"></a>Un consejo para la arquitectura de elementos de servidor

Como se indica en Implementación de [elementos](#_core_implementing_server_items)de servidor , las aplicaciones de servidor deben poder representar elementos tanto en la vista del servidor como en un metarchivo utilizado por la aplicación contenedora. En la arquitectura de aplicación de la biblioteca `OnDraw` Microsoft Foundation Class, la función miembro de la clase de vista representa el elemento cuando se está editando (consulte [CView::OnDraw](../mfc/reference/cview-class.md#ondraw) en la referencia de la *biblioteca*de clases ). El elemento de `OnDraw` servidor representa el elemento en un metarchivo en todos los demás casos (consulte [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).

Puede evitar la duplicación de código escribiendo funciones auxiliares `OnDraw` en la clase de documento de servidor y llamándolas desde las funciones de las clases de vista y elemento de servidor. El ejemplo OLE de MFC [HIERSVR](../overview/visual-cpp-samples.md) `CServerItem::OnDraw` utiliza `CServerDoc::DrawTree` esta estrategia: las funciones `CServerView::OnDraw` y ambas llaman para representar el elemento.

La vista y el `OnDraw` elemento tienen funciones miembro porque se dibujan en condiciones diferentes. La vista debe tener en cuenta factores como el zoom, el tamaño y la extensión de la selección, el recorte y los elementos de la interfaz de usuario, como las barras de desplazamiento. El elemento de servidor, por otro lado, siempre dibuja todo el objeto OLE.

Para obtener más información, vea [CView::OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)y [COleServerDoc::OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem) en la referencia de la biblioteca de *clases*.

## <a name="see-also"></a>Consulte también

[Servidores](../mfc/servers.md)
