---
title: Agregar elementos al control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 897612c6d5ac96704cc0a945df65146e6a01480a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57264383"
---
# <a name="adding-items-to-the-header-control"></a>Agregar elementos al control de encabezado

Después de crear el control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) en su ventana primaria, agregue tantos "elementos de encabezado" según sea necesario: normalmente uno por columna.

### <a name="to-add-a-header-item"></a>Para agregar un elemento de encabezado

1. Preparar una [estructura HD_ITEM](/windows/desktop/api/commctrl/ns-commctrl-_hd_itema) estructura.

1. Llame a [:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem), pasando la estructura.

1. Repita los pasos 1 y 2 para elementos adicionales.

Para obtener más información, consulte [agregando un elemento a un Control de encabezado](/windows/desktop/Controls/header-controls) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
