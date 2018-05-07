---
title: Controles de lista virtual | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cache, virtual list control item data
- list controls [MFC], virtual
- list controls [MFC], List view
- virtual list controls
ms.assetid: 319f841f-e426-423a-8276-d93f965b0b45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0b580e455aab7ff95beb85c02b8e3ca79dfa8a46
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="virtual-list-controls"></a>Controles de lista virtual
Un control de lista virtual es un control de vista de lista que tiene el **LVS_OWNERDATA** estilo. Este estilo permite al control admitir un recuento de elementos de un `DWORD` (el número de elementos de manera predeterminada sólo se extiende a un `int`). Sin embargo, la ventaja principal proporcionada por este estilo es la capacidad para tener sólo un subconjunto de elementos de datos en memoria en cualquier momento. Esto permite que el control de vista de lista virtual conducir por sí mismo para su uso con grandes bases de datos de información, donde los métodos específicos de acceso a los datos ya están en su lugar.  
  
> [!NOTE]
>  Además de proporcionar funcionalidad de lista virtual en `CListCtrl`, MFC también proporciona la misma funcionalidad en el [CListView](../mfc/reference/clistview-class.md) clase.  
  
 Hay algunos problemas de compatibilidad que debe tener en cuenta al desarrollar controles de lista virtual. Para obtener más información, vea la sección de problemas de compatibilidad del tema controles de vista de lista en el SDK de Windows.  
  
## <a name="handling-the-lvngetdispinfo-notification"></a>Controlar la notificación LVN_GETDISPINFO  
 Controles de lista virtual mantienen muy poca información de elementos. Excepto la selección de elementos e información de foco, el propietario del control administra toda la información de elemento. Se solicita información por el marco de trabajo a través de un **LVN_GETDISPINFO** mensaje de notificación. Para proporcionar la información solicitada, el propietario del control de lista virtual (o el propio control) debe controlar esta notificación. Esto puede realizarse fácilmente mediante la ventana Propiedades (consulte [asignar mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)). El código resultante debe ser similar al ejemplo siguiente (donde `CMyDialog` posee el objeto de control de lista virtual y el cuadro de diálogo está controlando la notificación):  
  
 [!code-cpp[NVC_MFCControlLadenDialog#23](../mfc/codesnippet/cpp/virtual-list-controls_1.cpp)]  
  
 En el controlador para el **LVN_GETDISPINFO** mensaje de notificación, debe comprobar para ver qué tipo de información que se solicita. Los valores posibles son:  
  
-   `LVIF_TEXT` El `pszText` debe rellenarse miembro.  
  
-   `LVIF_IMAGE` El `iImage` debe rellenarse miembro.  
  
-   **LVIF_INDENT** el *iIndent* miembro debe rellenarse.  
  
-   `LVIF_PARAM` El *lParam* miembro debe rellenarse. (No presente para elementos secundarios).  
  
-   `LVIF_STATE` El *estado* miembro debe rellenarse.  
  
 A continuación, también debe proporcionar la información que se solicita hacia el marco de trabajo.  
  
 El ejemplo siguiente (tomado del cuerpo del controlador de notificación para el objeto de control de lista), muestra un método posible proporcionando información en los búferes de texto e imagen de un elemento:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#24](../mfc/codesnippet/cpp/virtual-list-controls_2.cpp)]  
  
## <a name="caching-and-virtual-list-controls"></a>Controles de lista Virtual y almacenamiento en caché  
 Dado que este tipo de control de lista está pensado para grandes conjuntos de datos, se recomienda que se almacenan en caché los datos de elemento solicitado para mejorar el rendimiento de recuperación. El marco de trabajo proporciona un mecanismo de sugerencia de caché para ayudar a optimizar la memoria caché mediante el envío de un **LVN_ODCACHEHINT** mensaje de notificación.  
  
 En el ejemplo siguiente se actualiza la memoria caché con el intervalo que se pasa a la función de controlador.  
  
 [!code-cpp[NVC_MFCControlLadenDialog#25](../mfc/codesnippet/cpp/virtual-list-controls_3.cpp)]  
  
 Para obtener más información sobre la preparación y mantener una memoria caché, vea la sección de administración de la caché del tema controles de vista de lista en el SDK de Windows.  
  
## <a name="finding-specific-items"></a>Buscar elementos específicos  
 El **LVN_ODFINDITEM** mensaje de notificación se envía el control de lista virtual cuando es necesario encontrar un elemento de control de lista concreta. El mensaje de notificación se envía cuando el control de vista de lista recibe un acceso de clave rápido o cuando recibe un **LVM_FINDITEM** mensaje. Información de búsqueda se envía en forma de un **LVFINDINFO** estructura, que es un miembro de la **NMLVFINDITEM** estructura. Controlar este mensaje reemplazando la `OnChildNotify` función de la lista de objeto de control y dentro del cuerpo del controlador, busque el **LVN_ODFINDITEM** mensaje. Si se encuentra, lleve a cabo la acción apropiada.  
  
 Debe estar preparado para buscar un elemento que coincida con la información proporcionada por el control de vista de lista. Debe devolver el índice del elemento si se realiza correctamente, o -1 si no se encuentra ningún elemento coincidente.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

