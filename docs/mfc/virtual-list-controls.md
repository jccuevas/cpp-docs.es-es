---
title: Controles de lista virtual
ms.date: 11/04/2016
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
ms.openlocfilehash: 1ade5f404e134cf6de20756dcc5af169fefdec76
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375506"
---
# <a name="virtual-list-controls"></a>Controles de lista virtual

Un control de lista virtual es un control de vista de lista que tiene el estilo LVS_OWNERDATA. Este estilo permite que el control admita un recuento de elementos hasta un **DWORD** (el recuento de elementos predeterminado solo se extiende a un **int**). Sin embargo, la mayor ventaja que proporciona este estilo es la capacidad de tener solo un subconjunto de elementos de datos en la memoria a la vez. Esto permite que el control de vista de lista virtual se preste para su uso con grandes bases de datos de información, donde ya existen métodos específicos de acceso a los datos.

> [!NOTE]
> Además de proporcionar funcionalidad `CListCtrl`de lista virtual en , MFC también proporciona la misma funcionalidad en la [Clase CListView.](../mfc/reference/clistview-class.md)

Hay algunos problemas de compatibilidad que debe tener en cuenta al desarrollar controles de lista virtual. Para obtener más información, vea la sección Problemas de compatibilidad del tema Controles de vista de lista en el Windows SDK.

## <a name="handling-the-lvn_getdispinfo-notification"></a>Manejo de la notificación de LVN_GETDISPINFO

Los controles de lista virtual mantienen muy poca información de elementos. A excepción de la selección de elementos y la información de foco, toda la información del elemento es administrada por el propietario del control. El marco solicita información a través de un mensaje de notificación LVN_GETDISPINFO. Para proporcionar la información solicitada, el propietario del control de lista virtual (o el propio control) debe controlar esta notificación. Esto se puede hacer fácilmente mediante el [Asistente para clases](reference/mfc-class-wizard.md) (consulte Asignación de [mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). El código resultante debe tener un aspecto `CMyDialog` similar al siguiente ejemplo (donde posee el objeto de control de lista virtual y el cuadro de diálogo controla la notificación):

[!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]

En el controlador del mensaje de notificación LVN_GETDISPINFO, debe comprobar qué tipo de información se solicita. Los valores posibles son:

- `LVIF_TEXT`El miembro *pszText* debe rellenarse.

- `LVIF_IMAGE`El miembro *iImage* debe rellenarse.

- `LVIF_INDENT`El miembro *iIndent* debe rellenarse.

- `LVIF_PARAM`El miembro *lParam* debe rellenarse. (No está presente para subtemas.)

- `LVIF_STATE`El miembro del *estado* debe ser rellenado.

A continuación, debe proporcionar cualquier información que se solicite de nuevo al marco de trabajo.

En el ejemplo siguiente (tomado del cuerpo del controlador de notificaciones para el objeto de control de lista) se muestra un método posible proporcionando información para los búferes de texto y la imagen de un elemento:

[!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]

## <a name="caching-and-virtual-list-controls"></a>Almacenamiento en caché y controles de listas virtuales

Dado que este tipo de control de lista está pensado para grandes conjuntos de datos, se recomienda almacenar en caché los datos de elemento sordos para mejorar el rendimiento de la recuperación. El marco de trabajo proporciona un mecanismo de sugerencia de caché para ayudar a optimizar la memoria caché mediante el envío de un LVN_ODCACHEHINT mensaje de notificación.

En el ejemplo siguiente se actualiza la memoria caché con el intervalo pasado a la función de controlador.

[!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]

Para obtener más información sobre cómo preparar y mantener una memoria caché, vea la sección Administración de caché del tema Controles de vista de lista en el Windows SDK.

## <a name="finding-specific-items"></a>Búsqueda de artículos específicos

El LVN_ODFINDITEM mensaje de notificación lo envía el control de lista virtual cuando se necesita encontrar un elemento de control de lista determinado. El mensaje de notificación se envía cuando el control de vista de lista recibe acceso rápido a las claves o cuando recibe un mensaje de LVM_FINDITEM. La información de búsqueda se envía en forma de una estructura **LVFINDINFO,** que es un miembro de la estructura **NMLVFINDITEM.** Controle este mensaje `OnChildNotify` reemplazando la función del objeto de control de lista y dentro del cuerpo del controlador, compruebe si hay el mensaje de LVN_ODFINDITEM. Si se encuentra, realice la acción adecuada.

Debe estar preparado para buscar un elemento que coincida con la información proporcionada por el control de vista de lista. Debe devolver el índice del elemento si se realiza correctamente, o -1 si no se encuentra ningún elemento coincidente.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
