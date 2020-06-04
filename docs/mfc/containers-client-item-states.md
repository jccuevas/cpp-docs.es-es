---
title: 'Contenedores: Estados de elementos de cliente'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 1453ba3f96e49cefc9014a93ebcfbcfe5c6bc905
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152857"
---
# <a name="containers-client-item-states"></a>Contenedores: Estados de elementos de cliente

En este artículo se explica los diferentes Estados de que un elemento de cliente pasa a través de su duración.

Un elemento de cliente pasa por varios Estados, tal como se crea, activado, puede modificar y guardar. Cada vez que cambie de estado del elemento, llama el marco [COleClientItem](../mfc/reference/coleclientitem-class.md#onchange) con el **OLE_CHANGED_STATE** notificación. El segundo parámetro es un valor de la `COleClientItem::ItemState` enumeración. Puede ser uno de los siguientes:

- *COleClientItem::emptyState*

- *COleClientItem::loadedState*

- *COleClientItem::openState*

- *COleClientItem::activeState*

- *COleClientItem::activeUIState*

En el estado vacío, un elemento de cliente no es aún completamente un elemento. Se ha asignado la memoria para él, pero no se ha inicializado aún con los datos del elemento OLE. Este es el estado de un elemento de cliente está en cuando se creó mediante una llamada a **nuevo** pero aún no ha experimentado el segundo paso de la creación de dos pasos típicos.

En el segundo paso, se realiza a través de una llamada a `COleClientItem::CreateFromFile` u otro `CreateFrom` *xxxx* función, el elemento se crea por completo. Los datos OLE (desde un archivo o algún otro origen, como el Portapapeles) se ha asociado con el `COleClientItem`-objeto derivado. Ahora el elemento está en estado de carga.

Cuando un elemento se ha abierto en la ventana del servidor en lugar de abrirlo en contexto en el documento del contenedor, está en estado abierto (o completamente abierto). En este estado, normalmente se dibuja un sombreado sobre la representación del elemento en la ventana del contenedor para indicar que el elemento está activo en otro lugar.

Cuando un elemento se ha activado en su lugar, se aprueba, normalmente solo brevemente, mediante el estado activo. A continuación, introduce el estado activo de la interfaz de usuario, en el que el servidor ha combinado sus menús, barras de herramientas y otros componentes de interfaz de usuario con los del contenedor. La presencia de estos componentes de interfaz de usuario distingue el estado activo de la interfaz de usuario desde el estado activo. En caso contrario, el estado activo parece el estado activo de la interfaz de usuario. Si el servidor admite deshacer, el servidor es necesario para conservar la información de estado de deshacer del elemento OLE hasta que alcanza el estado abierto o cargado.

## <a name="see-also"></a>Vea también

[Contenedores](../mfc/containers.md)<br/>
[Activación](../mfc/activation-cpp.md)<br/>
[Contenedores: notificaciones de elementos de cliente](../mfc/containers-client-item-notifications.md)<br/>
[Seguimiento](../mfc/trackers.md)<br/>
[CRectTracker (clase)](../mfc/reference/crecttracker-class.md)
