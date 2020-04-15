---
title: Agregar columnas al control (Vista de informe)
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
ms.openlocfilehash: 34d7b62985748b9b9d741c083ec9b34fce06b309
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370870"
---
# <a name="adding-columns-to-the-control-report-view"></a>Agregar columnas al control (Vista de informe)

> [!NOTE]
> El siguiente procedimiento se aplica a un [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md) objeto.

Cuando un control de lista está en la vista de informe, se muestran columnas, lo que proporciona un método para organizar los distintos subelementos de cada elemento de control de lista. Esta organización se implementa con una correspondencia uno a uno entre una columna del control de lista y el subelemento asociado del elemento de control de lista. Para obtener más información sobre los subelementos, vea [Agregar elementos al control](../mfc/adding-items-to-the-control.md). Un ejemplo de un control de lista en la vista de informe se proporciona mediante la vista Detalles en el Explorador de Windows 95 y Windows 98. La primera columna enumera la carpeta, los iconos de archivo y las etiquetas. Otras columnas enumeran el tamaño del archivo, el tipo de archivo, la fecha de última modificación, etc.

Aunque las columnas se pueden agregar a un control de lista en `LVS_REPORT` cualquier momento, las columnas solo son visibles cuando el control tiene activado el bit de estilo.

Cada columna tiene un elemento de encabezado asociado (consulte [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) objeto que etiqueta la columna y permite a los usuarios cambiar el tamaño de la columna.

Si el control de lista admite una vista de informe, debe agregar una columna para cada subelemento posible en un elemento de control de lista. Agregue una columna preparando una estructura [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) y, a continuación, realice una llamada a [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Después de agregar las columnas necesarias (a veces denominadas elementos de encabezado), puede reordenarlas mediante funciones miembro y estilos que pertenecen al control de encabezado incrustado. Para obtener más información, consulte Pedido de [elementos en el control de encabezado](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
> Si el control de lista se crea con el **estilo LVS_NOCOLUMNHEADER,** se omitirá cualquier intento de insertar columnas.

## <a name="see-also"></a>Consulte también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
