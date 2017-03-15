---
title: "Servidores: Elementos de servidor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "arquitectura [C++], elemento del servidor"
  - "aplicaciones de servidor OLE, elementos del servidor"
  - "elementos del servidor"
  - "elementos del servidor, implementar"
  - "servidores [C++], elementos del servidor"
ms.assetid: 28ba81a1-726a-4728-a52d-68bc7efd5a3c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Servidores: Elementos de servidor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando un contenedor inicia un servidor para que un usuario puede editar un elemento OLE incrustado o vinculado, la aplicación de servidor crea un “elemento de servidor”. El elemento del servidor, que es un objeto de una clase derivada de `COleServerItem`, proporciona una interfaz entre el documento del servidor y la aplicación contenedora.  
  
 La clase de `COleServerItem` define varias funciones overridable miembro que son llamadas por OLE, normalmente en respuesta a solicitudes de contenedor.  Los elementos del Servidor pueden representar la parte del documento del servidor o de todo el documento.  Cuando un elemento OLE se incrusta en el documento contenedor, el elemento del servidor representa el documento completo del servidor.  Cuando se vincula el elemento OLE, el elemento del servidor puede representar una parte del documento del servidor o del documento completo, dependiendo de si el vínculo es a un elemento o conjunto.  
  
 En el ejemplo de [HIERSVR](../top/visual-cpp-samples.md) , por ejemplo, la clase de Servidor\- elemento, **CServerItem**, tiene un miembro que es un puntero a un objeto de clase **CServerNode**.  El objeto de **CServerNode** es un nodo en el documento de aplicación de HIERSVR, que es un árbol.  Cuando el objeto de **CServerNode** es el nodo raíz, el objeto de **CServerItem** representa el documento completo.  Cuando el objeto de **CServerNode** es un nodo secundario, el objeto de **CServerItem** representa una parte del documento.  Vea a MFC el ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md) para obtener un ejemplo de esta interacción.  
  
##  <a name="_core_implementing_server_items"></a> Implementar elementos de Servidor  
 Si utiliza el asistente para aplicaciones para mostrar el código “inicio” para la aplicación, todos lo que debe hacer para incluir elementos del servidor en el inicio el código es elegir una de las opciones de servidor de la página de opciones OLE.  Si está agregando elementos del servidor en una aplicación existente, siga estos pasos:  
  
#### Para implementar un elemento del servidor  
  
1.  Derivar una clase de `COleServerItem`.  
  
2.  En la clase derivada, reemplace la función miembro de `OnDraw` .  
  
     El marco de trabajo llama a `OnDraw` para representar el elemento OLE en un metarchivo.  La aplicación contenedora utiliza este metarchivo para representar el elemento.  La clase de vista de la aplicación también tiene una función miembro de `OnDraw` , que se utiliza para representar el elemento cuando la aplicación de servidor está activa.  
  
3.  Invalide de `OnGetEmbeddedItem` para la clase de Servidor\- documento.  Para obtener más información, vea el artículo [Servidores: Implementar documentos de Servidor](../mfc/servers-implementing-server-documents.md) y MFC ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md).  
  
4.  Implemente la función miembro de `OnGetExtent` de la clase de Servidor\- elemento.  El marco de trabajo llama a esta función para recuperar el tamaño del elemento.  La implementación predeterminada no hace nada.  
  
##  <a name="_core_a_tip_for_server.2d.item_architecture"></a> Una sugerencia para la arquitectura de Servidor\- elemento  
 Como se indica en [Implementar elementos de Servidor](#_core_implementing_server_items), las aplicaciones de servidor deben poder generar elementos tanto en la vista del servidor y en un metarchivo utilizado por la aplicación contenedora.  En la arquitectura de la aplicación MFC \(Microsoft Foundation Class\), la función miembro de `OnDraw` de la clase de vista genera el elemento cuando se edita \(vea [CView::OnDraw](../Topic/CView::OnDraw.md) en *la referencia de la biblioteca de clases*\).  `OnDraw` de elemento de servidor genera el elemento en un metarchivo en todos los demás casos \(vea [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md)\).  
  
 Puede evitar la duplicación de código escribiendo funciones auxiliares en la clase de Servidor\- documento y denominandolas de `OnDraw` funciona en las clases de vista y el Servidor\- elemento.  El ejemplo OLE [HIERSVR](../top/visual-cpp-samples.md) MFC utiliza esta estrategia: las funciones **CServerView::OnDraw** y **CServerItem::OnDraw** ambos llama **CServerDoc::DrawTree** para representar el elemento.  
  
 La vista y el elemento tienen funciones miembro de `OnDraw` porque dibujan en condiciones diferentes.  La vista debe tener en cuenta los factores como el zoom, tamaño y extensión de selección, recorte, y elementos de interfaz de usuario como barras de desplazamiento.  El elemento del servidor, por otro lado, dibuja siempre el objeto OLE completo.  
  
 Para obtener más información, vea [CView::OnDraw](../Topic/CView::OnDraw.md), [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerItem::OnDraw](../Topic/COleServerItem::OnDraw.md), y [COleServerDoc::OnGetEmbeddedItem](../Topic/COleServerDoc::OnGetEmbeddedItem.md) en *la referencia de la biblioteca de clases*.  
  
## Vea también  
 [Servidores](../mfc/servers.md)