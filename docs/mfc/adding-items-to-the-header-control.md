---
title: Agregar elementos al control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], header
- CHeaderCtrl class [MFC], adding items
- header controls [MFC], adding items to
ms.assetid: 2e9a28b1-7302-4a93-8037-c5a4183e589a
ms.openlocfilehash: 9b1cfd6f94d6412eef7b2bb9820f712e2a335454
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741171"
---
# <a name="adding-items-to-the-header-control"></a>Agregar elementos al control de encabezado

Después de crear el control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)) en la ventana primaria, agregue todos los "elementos de encabezado" que necesite: normalmente uno por columna.

### <a name="to-add-a-header-item"></a>Para agregar un elemento de encabezado

1. Preparar una estructura [HD_ITEM](/windows/win32/api/commctrl/ns-commctrl-hditemw) .

1. Llame a [CHeaderCtrl:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem)y pase la estructura.

1. Repita los pasos 1 y 2 para los elementos adicionales.

Para obtener más información, vea [Agregar un elemento a un control de encabezado](/windows/win32/Controls/header-controls) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
