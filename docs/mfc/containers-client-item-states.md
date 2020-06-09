---
title: 'Contenedores: Estados de elementos de cliente'
ms.date: 11/04/2016
helpviewer_keywords:
- OLE containers [MFC], client-item states
- states, OLE container client-item
- lifetime, lifetime states and OLE container client items
- client items and OLE containers
ms.assetid: e7021caa-bd07-4adb-976e-f5f3d025bc53
ms.openlocfilehash: 927211ccec35d8ec26e2f76b971c59b80248ab96
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625986"
---
# <a name="containers-client-item-states"></a>Contenedores: Estados de elementos de cliente

En este artículo se explican los distintos Estados a los que pasa un elemento de cliente en su duración.

Un elemento de cliente pasa por varios Estados a medida que se crea, activa, modifica y guarda. Cada vez que el estado del elemento cambia, el marco de trabajo llama a [COleClientItem:: onchange](reference/coleclientitem-class.md#onchange) con la notificación **OLE_CHANGED_STATE** . El segundo parámetro es un valor de la `COleClientItem::ItemState` enumeración. Puede tener uno de los valores siguientes:

- *COleClientItem:: emptyState*

- *COleClientItem:: loadedState*

- *COleClientItem:: openState*

- *COleClientItem:: activeState*

- *COleClientItem:: activeUIState*

En el estado vacío, un elemento de cliente todavía no es un elemento completamente. Se ha asignado la memoria, pero aún no se ha inicializado con los datos del elemento OLE. Este es el estado en el que se encuentra un elemento de cliente cuando se ha creado a través de una llamada a **New** , pero aún no ha experimentado el segundo paso de la creación típica de dos pasos.

En el segundo paso, realizado a través de una llamada a `COleClientItem::CreateFromFile` u otra `CreateFrom` función *xxxx* , el elemento se crea completamente. Los datos OLE (de un archivo o de otro origen, como el portapapeles) se han asociado con el `COleClientItem` objeto derivado de. Ahora el elemento está en estado cargado.

Cuando un elemento se ha abierto en la ventana del servidor en lugar de abrirse en su lugar en el documento del contenedor, se encuentra en el estado abierto (o completamente abierto). En este estado, normalmente se dibuja una trama cruzada sobre la representación del elemento en la ventana del contenedor para indicar que el elemento está activo en otra parte.

Cuando un elemento se ha activado en contexto, pasa, normalmente solo brevemente, a través del estado activo. Después, entra en el estado activo de la interfaz de usuario, en el que el servidor ha combinado sus menús, barras de herramientas y otros componentes de la interfaz de usuario con los del contenedor. La presencia de estos componentes de interfaz de usuario distingue el estado activo de la interfaz de usuario del estado activo. De lo contrario, el estado activo es similar al estado activo de la interfaz de usuario. Si el servidor admite la operación de deshacer, el servidor debe conservar la información de estado de deshacer del elemento OLE hasta que alcance el estado cargado o abierto.

## <a name="see-also"></a>Consulte también

[Contenedores](containers.md)<br/>
[Activación](activation-cpp.md)<br/>
[Contenedores: Notificaciones de elementos de cliente](containers-client-item-notifications.md)<br/>
[Seguimiento](trackers.md)<br/>
[CRectTracker (clase)](reference/crecttracker-class.md)
