---
title: Controles de lista virtual
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: b9da918017d300d7af61b1fd3ab27869e136bb8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50573695"
---
# <a name="virtual-list-controls"></a>Controles de lista virtual

Un control de lista virtual es un control de vista de lista que tiene el estilo LVS_OWNERDATA. Este estilo permite que el control admitir un número de elementos hasta un **DWORD** (el número de elementos de forma predeterminada sólo se extiende a un **int**). Sin embargo, la mayor ventaja que aporta este estilo es la capacidad de tener solo un subconjunto de elementos de datos en memoria en cualquier momento. Esto permite que el control de vista de lista virtual que se presta para su uso con grandes bases de datos de información, donde los métodos específicos de acceso a datos ya están en su lugar.

> [!NOTE]
>  Además de proporcionar funcionalidad de lista virtual en `CListCtrl`, MFC también proporciona la misma funcionalidad en el [CListView](../mfc/reference/clistview-class.md) clase.

Hay algunos problemas de compatibilidad que debe tener en cuenta al desarrollar controles de lista virtual. Para obtener más información, consulte la sección de problemas de compatibilidad del tema de los controles de vista de lista en el SDK de Windows.

## <a name="handling-the-lvngetdispinfo-notification"></a>Controlar la notificación LVN_GETDISPINFO

Controles de lista virtual mantienen muy poca información del elemento. Excepto la información de foco y selección de elementos, el propietario del control administra toda la información de elemento. El marco de trabajo a través de un mensaje de notificación LVN_GETDISPINFO se solicita información. Para proporcionar la información solicitada, el propietario del control de lista virtual (o el propio control) debe controlar esta notificación. Esto puede hacerse fácilmente mediante la ventana Propiedades (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). El código resultante debe ser similar al ejemplo siguiente (donde `CMyDialog` posee el objeto de control de lista virtual y el cuadro de diálogo está controlando la notificación):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

En el controlador para el mensaje de notificación LVN_GETDISPINFO, debe comprobar para ver qué tipo de información se solicita. Los valores posibles son:

- `LVIF_TEXT` El *pszText* miembro debe rellenarse.

- `LVIF_IMAGE` El *iImage* miembro debe rellenarse.

- `LVIF_INDENT` El *iIndent* miembro debe rellenarse.

- `LVIF_PARAM` El *lParam* miembro debe rellenarse. (No presente para elementos secundarios).

- `LVIF_STATE` El *estado* miembro debe rellenarse.

A continuación, debería proporcionar cualquier información que se solicita hasta el marco de trabajo.

El ejemplo siguiente (tomado del cuerpo del controlador de notificación para el objeto de control de lista), muestra un posible método para proporcionar información de la imagen de un elemento y los búferes de texto:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Controles de lista Virtual y almacenamiento en caché

Como este tipo de control de lista está pensado para grandes conjuntos de datos, se recomienda que copie en caché datos de elemento solicitado para mejorar el rendimiento de recuperación. El marco de trabajo proporciona un mecanismo de sugerencia de caché para ayudar a optimizar la memoria caché mediante el envío de un mensaje de notificación LVN_ODCACHEHINT.

El ejemplo siguiente actualiza la memoria caché con el intervalo pasado a la función de controlador.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Para obtener más información sobre la preparación y mantener una memoria caché, vea la sección de administración de la caché del tema de los controles de vista de lista en el SDK de Windows.

## <a name="finding-specific-items"></a>Buscar elementos específicos

El control de lista virtual envía el mensaje de notificación LVN_ODFINDITEM cuando es necesario encontrar un elemento de control de lista determinado. El mensaje de notificación se envía cuando el control de vista de lista recibe acceso rápido a la clave o cuando recibe un mensaje LVM_FINDITEM. Información de búsqueda se envía en forma de un **LVFINDINFO** estructura, que es un miembro de la **NMLVFINDITEM** estructura. Controlar este mensaje reemplazando el `OnChildNotify` controlar el objeto de función de la lista y dentro del cuerpo del controlador, compruebe el mensaje LVN_ODFINDITEM. Si se encuentra, lleve a cabo la acción apropiada.

Debe estar preparado para buscar un elemento que coincide con la información proporcionada por el control de vista de lista. Debe devolver el índice del elemento si se realiza correctamente, o -1 si no se encuentra ningún elemento coincidente.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

