---
title: Control de encabezado y control de lista
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], with CHeaderCtrl
- CListCtrl class [MFC], header controls
- CHeaderCtrl class [MFC], with CListCtrl
- controls [MFC], header
- header controls [MFC]
- header controls [MFC], list controls used with
ms.assetid: b20194b1-1a6b-4e2f-b890-1b3cca6650bc
ms.openlocfilehash: 53dd6f1a7878d82a7f7ac48dd7082d791323941b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370472"
---
# <a name="header-control-and-list-control"></a>Control de encabezado y control de lista

En la mayoría de los casos, usará el control de encabezado que está incrustado en un [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) objeto. Sin embargo, hay casos en los que un objeto de control de encabezado independiente es deseable, como la manipulación de datos, organizados en columnas o filas, en un [CView](../mfc/reference/cview-class.md)-objeto derivado. En estos casos, necesita un mayor control sobre la apariencia y el comportamiento predeterminado de un control de encabezado incrustado.

En el caso común de que desee que un control de encabezado proporcione un comportamiento estándar y predeterminado, es posible que desee usar [CListCtrl](../mfc/reference/clistctrl-class.md) o [CListView](../mfc/reference/clistview-class.md) en su lugar. Utilícelo `CListCtrl` cuando desee la funcionalidad de un control de encabezado predeterminado, incrustado en un control común de vista de lista. Utilice [CListView](../mfc/reference/clistview-class.md) cuando desee la funcionalidad de un control de encabezado predeterminado, incrustado en un objeto de vista.

> [!NOTE]
> Estos controles solo incluyen un control de encabezado integrado si el control de vista de lista se crea con el estilo **LVS_REPORT.**

En la mayoría de los casos, la apariencia del control de encabezado incrustado se puede modificar cambiando los estilos del control de vista de lista contenedor. Además, la información sobre el control de encabezado se puede obtener a través de las funciones miembro del control de vista de lista primario. Sin embargo, para un control completo y acceso a los atributos y estilos del control de encabezado incrustado, se recomienda obtener un puntero al objeto de control de encabezado.

Se puede tener acceso al objeto `CListCtrl` `CListView` de control de encabezado incrustado `GetHeaderCtrl` desde una o con una llamada a la función miembro de la clase respectiva. El código siguiente muestra este proceso:

[!code-cpp[NVC_MFCControlLadenDialog#14](../mfc/codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué quieres saber más sobre

- [Uso de listas de imágenes con controles de encabezado](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
