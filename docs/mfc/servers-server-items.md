---
title: 'Servidores: Elementos de servidor | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- server items, implementing
- servers [MFC], server items
- architecture [MFC], server-item
- server items
- OLE server applications [MFC], server items
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2fe196eb561c336e45402de6c390146a0d77bea4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="servers-server-items"></a>Servidores: Elementos de servidor
Cuando un contenedor inicia un servidor para que un usuario puede editar un elemento OLE incrustado o vinculado, la aplicación de servidor crea un "elemento de servidor". El elemento del servidor, que es un objeto de una clase derivada de `COleServerItem`, proporciona una interfaz entre el documento de servidor y la aplicación contenedora.  
  
 La `COleServerItem` clase define varias funciones miembro reemplazables que reciben llamadas de OLE, normalmente en respuesta a las solicitudes desde el contenedor. Elementos del servidor pueden representar parte del documento de servidor o todo el documento. Cuando un elemento OLE se incrusta en el documento contenedor, el elemento de servidor representa el documento de todo el servidor. Cuando se vincula el elemento OLE, el elemento del servidor puede representar una parte del documento de servidor o todo el documento, dependiendo de si el vínculo es a una parte o todo.  
  
 En el [HIERSVR](../visual-cpp-samples.md) ejemplo, por ejemplo, la clase de elemento de servidor, **CServerItem**, tiene un miembro que es un puntero a un objeto de la clase **CServerNode**. El **CServerNode** objeto es un nodo de documento de la aplicación HIERSVR, que es un árbol. Cuando el **CServerNode** objeto es el nodo raíz, el **CServerItem** objeto representa todo el documento. Cuando el **CServerNode** objeto es un nodo secundario, el **CServerItem** objeto representa una parte del documento. Vea el ejemplo de MFC OLE [HIERSVR](../visual-cpp-samples.md) para obtener un ejemplo de esta interacción.  
  
##  <a name="_core_implementing_server_items"></a>Implementar elementos de servidor  
 Si utiliza el Asistente para aplicaciones para generar código de "inicio" para la aplicación, lo único que debe hacer para incluir elementos del servidor en el código de inicio es elegir una de las opciones de servidor desde la página Opciones OLE. Si va a agregar elementos del servidor a una aplicación existente, realice los pasos siguientes:  
  
#### <a name="to-implement-a-server-item"></a>Para implementar un elemento de servidor  
  
1.  Derivar una clase de `COleServerItem`.  
  
2.  En la clase derivada, reemplace el `OnDraw` función miembro.  
  
     Las llamadas de framework `OnDraw` para representar el elemento OLE en un metarchivo. La aplicación contenedora utiliza este metarchivo para representar el elemento. Clase de vista de la aplicación también tiene una `OnDraw` función de miembro, que se usa para representar el elemento cuando la aplicación de servidor está activa.  
  
3.  Implemente un reemplazo del `OnGetEmbeddedItem` para la clase de documento de servidor. Para obtener más información, vea el artículo [servidores: implementar documentos de servidor](../mfc/servers-implementing-server-documents.md) y el ejemplo de MFC OLE [HIERSVR](../visual-cpp-samples.md).  
  
4.  Implementar la clase de elemento de servidor `OnGetExtent` función miembro. El marco de trabajo llama a esta función para recuperar el tamaño del elemento. La implementación predeterminada no hace nada.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a>Una sugerencia para la arquitectura de un elemento de servidor  
 Como se indicó en [implementar elementos de servidor](#_core_implementing_server_items), las aplicaciones de servidor deben ser capaces de procesar elementos en la vista del servidor y en un metarchivo utilizado por la aplicación contenedora. En arquitectura de la aplicación de la biblioteca Microsoft Foundation Class, la clase de vista `OnDraw` función miembro procesa el elemento cuando se está editando (vea [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw) en el *referencia de la biblioteca de clase* ). El elemento de servidor `OnDraw` representa el elemento en un metarchivo en los demás casos (vea [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw)).  
  
 Puede evitar la duplicación de código escribiendo funciones auxiliares en la clase de documento de servidor y llamarlas desde el `OnDraw` funciones en las clases de vista y el elemento del servidor. El ejemplo de MFC OLE [HIERSVR](../visual-cpp-samples.md) usa esta estrategia: las funciones **CServerView** y **CServerItem** ambas llaman **CServerDoc:: DrawTree**  para representar el elemento.  
  
 La vista y el elemento tienen `OnDraw` funciones miembro, puesto que se dibujan en condiciones diferentes. La vista debe tener en cuenta factores como el zoom, tamaño de la selección y extensión, recorte y elementos de interfaz de usuario, como barras de desplazamiento. Por otro lado, el elemento del servidor, siempre dibuja todo el objeto OLE.  
  
 Para obtener más información, consulte [CView:: OnDraw](../mfc/reference/cview-class.md#ondraw), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem:: OnDraw](../mfc/reference/coleserveritem-class.md#ondraw), y [COleServerDoc:: OnGetEmbeddedItem](../mfc/reference/coleserverdoc-class.md#ongetembeddeditem)en la *referencia de biblioteca de clases de*.  
  
## <a name="see-also"></a>Vea también  
 [Servidores](../mfc/servers.md)

