---
title: Agregar columnas al Control (vista de informes) | Microsoft Docs
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
ms.openlocfilehash: bf967a3a1557bdba8f372c6f277f62eb257befee
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392000"
---
# <a name="adding-columns-to-the-control-report-view"></a>Agregar columnas al control (Vista de informe)

> [!NOTE]
>  El siguiente procedimiento se aplica ya sea un [CListView](../mfc/reference/clistview-class.md) o [CListCtrl](../mfc/reference/clistctrl-class.md) objeto.

Cuando un control de lista está en vista de informe, se muestran las columnas, que proporciona un método para organizar los distintos subelementos de cada elemento del control de lista. Esta organización se implementa con una correspondencia uno a uno entre una columna en el control de lista y el subelemento del elemento de control de lista asociado. Para obtener más información sobre los subelementos, consulte [agregar elementos al Control](../mfc/adding-items-to-the-control.md). Se proporciona un ejemplo de un control de lista en vista de informe en la vista de detalles en Windows 95 y Windows 98 Explorer. La primera columna enumera etiquetas, iconos de archivo y carpeta. Otras columnas de lista tamaño de archivo, tipo de archivo, fecha de última modificado y así sucesivamente.

Aunque se pueden agregar columnas a un control de lista en cualquier momento, las columnas están visibles solo cuando el control tiene el `LVS_REPORT` activado el bit de estilo.

Cada columna tiene un elemento de encabezado asociado (consulte [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) objeto que la columna de etiqueta y permite a los usuarios cambiar el tamaño de la columna.

Si el control de lista admite una vista de informe, deberá agregar una columna para cada subelemento posibles en un elemento de control de lista. Agregar una columna al preparar una [estructura LV_COLUMN](/windows/desktop/api/commctrl/ns-commctrl-taglvcolumna) estructura y, a continuación, realizar una llamada a [InsertColumn](../mfc/reference/clistctrl-class.md#insertcolumn). Después de agregar las columnas necesarias (a veces denominadas elementos de encabezado), puede reordenar con las funciones miembro y estilos que pertenecen al control de encabezado incrustado. Para obtener más información, consulte [ordenar elementos en el Control de encabezado](../mfc/ordering-items-in-the-header-control.md).

> [!NOTE]
>  Si el control de lista se crea con el **LVS_NOCOLUMNHEADER** estilos, cualquier intento para insertar columnas se pasará por alto.

## <a name="see-also"></a>Vea también

[Uso de CListCtrl](../mfc/using-clistctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

