---
title: 'Contenedores: Estados de elementos de cliente | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5046ea7f3f3775cfe0009afe50f33a6ce6723cc0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33342178"
---
# <a name="containers-client-item-states"></a>Contenedores: Estados de elementos de cliente
Este artículo explica los diferentes Estados de que un elemento de cliente pasa a través de su duración.  
  
 Un elemento de cliente pasa por varios Estados, tal y como se creó, activado, modificado y guardado. Cada vez que cambia de estado del elemento, las llamadas de framework [COleClientItem](../mfc/reference/coleclientitem-class.md#onchange) con el `OLE_CHANGED_STATE` notificación. El segundo parámetro es un valor comprendido entre el **COleClientItem:: ItemState** enumeración. Puede ser uno de los siguientes:  
  
-   **COleClientItem::emptyState**  
  
-   **COleClientItem::loadedState**  
  
-   **COleClientItem::openState**  
  
-   **COleClientItem::activeState**  
  
-   **COleClientItem::activeUIState**  
  
 En el estado vacío, un elemento de cliente no es todavía completamente un elemento. Se ha asignado la memoria para el mismo, pero no se ha inicializado con los datos del elemento OLE. Este es el estado en un elemento de cliente cuando se ha creado mediante una llamada a **nueva** pero no ha experimentado todavía el segundo paso de la creación de dos pasos típicos.  
  
 En el segundo paso, se realiza a través de una llamada a `COleClientItem::CreateFromFile` u otro **CreateFrom *** xxxx* función, el elemento se crea por completo. Los datos OLE (de un archivo o algún otro origen, como el Portapapeles) se ha asociado el `COleClientItem`-objeto derivado. Ahora el elemento está en estado de carga.  
  
 Cuando un elemento se ha abierto en la ventana del servidor en lugar de abierto en lugar de documento del contenedor, está en el estado abierto (o completamente abierto). En este estado, normalmente se dibuja un sombreado sobre la representación del elemento en la ventana del contenedor para indicar que el elemento está activo en otro lugar.  
  
 Cuando un elemento se ha activado en su lugar, se aprueba, normalmente solo brevemente, mediante el estado activo. A continuación, entra en el estado activo de interfaz de usuario, en el que el servidor combinó sus menús, barras de herramientas y otros componentes de interfaz de usuario con los del contenedor. La presencia de estos componentes de interfaz de usuario distingue el estado activo de la interfaz de usuario desde el estado activo. En caso contrario, el estado activo parecería el estado activo de interfaz de usuario. Si el servidor permite deshacer, el servidor es necesario para conservar la información de deshacer el estado del elemento OLE hasta alcanzar el estado abierto o cargado.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores](../mfc/containers.md)   
 [activación](../mfc/activation-cpp.md)   
 [Contenedores: Notificaciones de elementos de cliente](../mfc/containers-client-item-notifications.md)   
 [Objetos de seguimiento](../mfc/trackers.md)   
 [CRectTracker (clase)](../mfc/reference/crecttracker-class.md)
