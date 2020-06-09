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
ms.openlocfilehash: f9dd34b27ddbdc0b99fafbb23ad1cf9782d98605
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626421"
---
# <a name="header-control-and-list-control"></a>Control de encabezado y control de lista

En la mayoría de los casos, utilizará el control de encabezado que está incrustado en un objeto [CListCtrl](reference/clistctrl-class.md) o [CListView](reference/clistview-class.md) . Sin embargo, hay casos en los que es deseable un objeto de control de encabezado independiente, como la manipulación de datos, organizados en columnas o filas, en un objeto derivado de [CView](reference/cview-class.md). En estos casos, se necesita un mayor control sobre la apariencia y el comportamiento predeterminado de un control de encabezado incrustado.

En el caso habitual de que desee que un control de encabezado proporcione un comportamiento estándar y predeterminado, puede que desee usar [CListCtrl](reference/clistctrl-class.md) o [CListView](reference/clistview-class.md) en su lugar. Use `CListCtrl` cuando quiera la funcionalidad de un control de encabezado predeterminado, incrustado en un control común de vista de lista. Use [CListView](reference/clistview-class.md) cuando quiera la funcionalidad de un control de encabezado predeterminado, incrustado en un objeto de vista.

> [!NOTE]
> Estos controles solo incluyen un control de encabezado integrado si el control de vista de lista se crea con el estilo **LVS_REPORT** .

En la mayoría de los casos, la apariencia del control de encabezado incrustado se puede modificar cambiando los estilos del control de vista de lista contenedor. Además, la información sobre el control de encabezado se puede obtener a través de las funciones miembro del control de vista de lista primario. Sin embargo, para obtener el control completo y el acceso a los atributos y estilos del control de encabezado incrustado, se recomienda obtener un puntero al objeto de control de encabezado.

Se puede tener acceso al objeto de control de encabezado incrustado desde `CListCtrl` o `CListView` con una llamada a la función miembro de la clase correspondiente `GetHeaderCtrl` . El código siguiente muestra este proceso:

[!code-cpp[NVC_MFCControlLadenDialog#14](codesnippet/cpp/header-control-and-list-control_1.cpp)]

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Usar listas de imágenes con controles de encabezado](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Permite](controls-mfc.md)
