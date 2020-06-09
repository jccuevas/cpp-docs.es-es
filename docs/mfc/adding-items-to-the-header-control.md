---
title: Agregar elementos al control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 5749a0cae2dfe7e6c9f4c166eca487e36c2d21d2
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616466"
---
# <a name="adding-items-to-the-header-control"></a>Agregar elementos al control de encabezado

Después de crear el control de encabezado ([CHeaderCtrl](reference/cheaderctrl-class.md)) en la ventana primaria, agregue todos los "elementos de encabezado" que necesite: normalmente uno por columna.

### <a name="to-add-a-header-item"></a>Para agregar un elemento de encabezado

1. Preparar una estructura de [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .

1. Llame a [CHeaderCtrl:: InsertItem](reference/cheaderctrl-class.md#insertitem)y pase la estructura.

1. Repita los pasos 1 y 2 para los elementos adicionales.

Para obtener más información, vea [Agregar un elemento a un control de encabezado](/windows/win32/Controls/header-controls) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](using-cheaderctrl.md)<br/>
[Permite](controls-mfc.md)
