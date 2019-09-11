---
title: Controles de lista virtual
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: a6e76a812a6196c487f72516e2b88198a544fdc7
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907341"
---
# <a name="virtual-list-controls"></a>Controles de lista virtual

Un control de lista virtual es un control de vista de lista que tiene el estilo LVS_OWNERDATA. Este estilo permite que el control admita un recuento de elementos hasta un **valor DWORD** (el recuento de elementos predeterminados solo se extiende a un **int**). Sin embargo, la mayor ventaja que proporciona este estilo es la posibilidad de tener solo un subconjunto de elementos de datos en la memoria al mismo tiempo. Esto permite que el control de vista de lista virtual se preste a sí mismo para su uso con bases de datos de gran tamaño, donde ya están en su lugar los métodos específicos de acceso a los datos.

> [!NOTE]
>  Además de proporcionar la funcionalidad de lista virtual `CListCtrl`en, MFC también proporciona la misma funcionalidad en la clase [CListView](../mfc/reference/clistview-class.md) .

Hay algunos problemas de compatibilidad que debe tener en cuenta al desarrollar controles de lista virtual. Para obtener más información, vea la sección problemas de compatibilidad del tema controles de vista de lista en el Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Controlar la notificación de LVN_GETDISPINFO

Los controles de lista virtual mantienen muy poca información de los elementos. A excepción de la selección de elementos y la información de foco, el propietario del control administra toda la información de los elementos. La información la solicita el marco de trabajo a través de un mensaje de notificación LVN_GETDISPINFO. Para proporcionar la información solicitada, el propietario del control de lista virtual (o el propio control) debe controlar esta notificación. Esto se puede hacer fácilmente mediante el [Asistente para clases](reference/mfc-class-wizard.md) (consulte [asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). El código resultante debe ser similar al del ejemplo siguiente (donde `CMyDialog` posee el objeto de control de lista virtual y el cuadro de diálogo controla la notificación):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

En el controlador del mensaje de notificación LVN_GETDISPINFO, debe comprobar qué tipo de información se solicita. Los valores posibles son:

- `LVIF_TEXT`El miembro *miembros pszText* se debe rellenar.

- `LVIF_IMAGE`El miembro *iImage* se debe rellenar.

- `LVIF_INDENT`El miembro *iIndent* se debe rellenar.

- `LVIF_PARAM`Se debe rellenar el miembro *lParam* . (No está presente para los subelementos).

- `LVIF_STATE`El miembro de *Estado* se debe rellenar.

A continuación, debe proporcionar la información que se solicita de vuelta al marco.

En el ejemplo siguiente (tomado del cuerpo del controlador de notificación para el objeto de control de lista) se muestra un método posible proporcionando información para los búferes de texto y la imagen de un elemento:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Almacenamiento en caché y controles de lista virtual

Dado que este tipo de control de lista está pensado para conjuntos de datos grandes, se recomienda almacenar en caché los datos de elementos solicitados para mejorar el rendimiento de la recuperación. El marco de trabajo proporciona un mecanismo de sugerencias de caché para ayudar a optimizar la memoria caché mediante el envío de un mensaje de notificación de LVN_ODCACHEHINT.

En el ejemplo siguiente se actualiza la caché con el intervalo pasado a la función de controlador.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Para obtener más información sobre la preparación y el mantenimiento de una caché, consulte la sección Administración de la memoria caché del tema controles de vista de lista en el Windows SDK.

## <a name="finding-specific-items"></a>Buscar elementos específicos

El control de lista virtual envía el mensaje de notificación LVN_ODFINDITEM cuando es necesario encontrar un elemento de control de lista determinado. El mensaje de notificación se envía cuando el control de vista de lista recibe el acceso rápido a la tecla o cuando recibe un mensaje LVM_FINDITEM. La información de búsqueda se envía en forma de una estructura **LVFINDINFO** , que es un miembro de la estructura **NMLVFINDITEM** . Controle este mensaje invalidando `OnChildNotify` la función del objeto de control de lista y dentro del cuerpo del controlador, busque el mensaje LVN_ODFINDITEM. Si se encuentra, realice la acción adecuada.

Debe estar preparado para buscar un elemento que coincida con la información proporcionada por el control de vista de lista. Debe devolver el índice del elemento si se realiza correctamente, o-1 si no se encuentra ningún elemento coincidente.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
