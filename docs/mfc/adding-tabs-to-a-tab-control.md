---
title: Agregar pestañas a un control de pestaña
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 8915b3af083ebe318e8527b2f83099bf61e7e3ce
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509296"
---
# <a name="adding-tabs-to-a-tab-control"></a>Agregar pestañas a un control de pestaña

Después de crear el control de pestaña ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), agregue tantas pestañas como necesite.

### <a name="to-add-a-tab-item"></a>Para agregar un elemento de ficha

1. Preparar una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Llame a [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem)y pase la estructura.

1. Repita los pasos 1 y 2 para los elementos de ficha adicionales.

Para obtener más información, vea [crear un control de ficha](/windows/win32/Controls/tab-controls) en el Windows SDK.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
