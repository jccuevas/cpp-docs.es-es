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
ms.openlocfilehash: 9321a582f223269ee998dccd01721f47d90eb7fe
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509337"
---
# <a name="adding-columns-to-the-control-report-view"></a>Agregar columnas al control (Vista de informe)

> [!NOTE]
>  El siguiente procedimiento se aplica a un objeto [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md) .

Cuando un control de lista está en la vista de informe, se muestran las columnas, que proporcionan un método para organizar los distintos subelementos de cada elemento de control de lista. Esta organización se implementa con una correspondencia uno a uno entre una columna del control de lista y el subelemento asociado del elemento de control de lista. Para obtener más información sobre los subelementos, vea [Agregar elementos al control](../mfc/adding-items-to-the-control.md). La vista de detalles de Windows 95 y el explorador de Windows 98 proporciona un ejemplo de un control de lista en la vista de informes. La primera columna muestra la carpeta, los iconos de archivo y las etiquetas. Otras columnas muestran el tamaño del archivo, el tipo de archivo, la fecha de la última modificación, etc.

Aunque las columnas se pueden agregar a un control de lista en cualquier momento, las columnas solo están visibles cuando el control tiene `LVS_REPORT` el bit de estilo activado.

Cada columna tiene un objeto de encabezado asociado (vea [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) que etiqueta la columna y permite a los usuarios cambiar el tamaño de la columna.

Si el control de lista admite una vista de informe, debe agregar una columna para cada subelemento posible de un elemento de control de lista. Agregue una columna preparando una estructura [LVCOLUMN](/windows/win32/api/commctrl/ns-commctrl-lvcolumnw) y, a continuación, realice una llamada a [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Después de agregar las columnas necesarias (a veces denominadas elementos de encabezado), puede reordenarlas mediante las funciones miembro y los estilos que pertenecen al control de encabezado incrustado. Para obtener más información, vea [ordenar elementos en el control de encabezado](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Si el control de lista se crea con el estilo **LVS_NOCOLUMNHEADER** , se omitirá cualquier intento de Insertar columnas.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
