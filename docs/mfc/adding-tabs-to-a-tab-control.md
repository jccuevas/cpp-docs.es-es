---
title: Agregar pestañas a un control de pestaña
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: 89132e94396b51bee4a111b963c67d029f3dd9df
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616532"
---
# <a name="adding-tabs-to-a-tab-control"></a>Agregar pestañas a un control de pestaña

Después de crear el control de pestaña ([CTabCtrl](reference/ctabctrl-class.md)), agregue tantas pestañas como necesite.

### <a name="to-add-a-tab-item"></a>Para agregar un elemento de ficha

1. Preparar una estructura [TCITEM](/windows/win32/api/commctrl/ns-commctrl-tcitemw) .

1. Llame a [CTabCtrl:: InsertItem](reference/ctabctrl-class.md#insertitem)y pase la estructura.

1. Repita los pasos 1 y 2 para los elementos de ficha adicionales.

Para obtener más información, vea [crear un control de ficha](/windows/win32/Controls/tab-controls) en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Uso de CTabCtrl](using-ctabctrl.md)<br/>
[Permite](controls-mfc.md)
