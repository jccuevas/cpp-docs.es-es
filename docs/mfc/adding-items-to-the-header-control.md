---
title: Agregar elementos al control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: d9a35123ddbe77b8e5e1779651fc4cde233863ae
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509318"
---
# <a name="adding-items-to-the-header-control"></a>Agregar elementos al control de encabezado

Después de crear el control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) en la ventana primaria, agregue todos los "elementos de encabezado" que necesite: normalmente uno por columna.

### <a name="to-add-a-header-item"></a>Para agregar un elemento de encabezado

1. Preparar una estructura [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-_hd_itemw) .

1. Llame a [CHeaderCtrl:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem)y pase la estructura.

1. Repita los pasos 1 y 2 para los elementos adicionales.

Para obtener más información, vea [Agregar un elemento a un control de encabezado](/windows/win32/Controls/header-controls) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
