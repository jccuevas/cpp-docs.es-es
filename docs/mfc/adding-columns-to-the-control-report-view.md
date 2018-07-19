---
title: Agregar columnas al Control (vista de informe) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CListCtrl class [MFC], adding columns
- report view in CListCtrl class [MFC]
- views [MFC], report
- columns [MFC], adding to CListCtrl
- CListCtrl class [MFC], report view
ms.assetid: 7392c0d7-f8a5-4e7b-9ae7-b53dc9dd80ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 975d65119ba0ae24b236d96cbe67e73b70be6bac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341834"
---
# <a name="adding-columns-to-the-control-report-view"></a>Agregar columnas al control (Vista de informe)
> [!NOTE]
>  El siguiente procedimiento se aplica a un [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md) objeto.  
  
 Cuando un control de lista está en vista de informe, se muestran las columnas, lo que constituye un método de organizar los distintos subelementos de cada elemento de control de lista. Esta organización se implementa con una correspondencia uno a uno entre una columna en el control de lista y el subelemento asociado del elemento de control de lista. Para obtener más información sobre los subelementos, vea [agregar elementos al Control](../mfc/adding-items-to-the-control.md). Se proporciona un ejemplo de un control de lista en la vista de informe en la vista de detalles en Windows 95 y en el Explorador de Windows 98. La primera columna muestra etiquetas, iconos de archivo y carpeta. Otras columnas enumeran tamaño de archivo, tipo de archivo, fecha de última modificada y así sucesivamente.  
  
 Aunque las columnas se pueden agregar a un control de lista en cualquier momento, las columnas están visibles solamente cuando el control tiene el `LVS_REPORT` activado el bit de estilo.  
  
 Cada columna tiene un elemento de encabezado asociado (vea [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) objeto que las etiquetas de la columna y permite a los usuarios cambiar el tamaño de la columna.  
  
 Si el control de lista admite una vista de informe, debe agregar una columna para cada posible subelemento de un elemento de control de lista. Agregar una columna al preparar una [estructura LV_COLUMN](http://msdn.microsoft.com/library/windows/desktop/bb774743) estructura y, a continuación, realizar una llamada a [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Después de agregar las columnas necesarias (denominadas a veces como elementos de encabezado), se pueden volver a ordenarlas utilizando funciones miembro y estilos pertenecientes al control de encabezado incrustado. Para obtener más información, consulte [ordenar elementos en el Control de encabezado](../mfc/ordering-items-in-the-header-control.md).  
  
> [!NOTE]
>  Si el control de lista se crea con el **LVS_NOCOLUMNHEADER** estilos, cualquier intento para insertar columnas se pasará por alto.  
  
## <a name="see-also"></a>Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)

