---
title: Agregar pestañas a un control de pestaña
ms.date: 11/04/2016
helpviewer_keywords:
- tab controls [MFC], adding tabs
- putting tabs on CTabCtrls [MFC]
- CTabCtrl class [MFC], adding tabs
- tabs [MFC], adding to CTabCtrl class [MFC]
ms.assetid: 7f3d9340-e3c7-4c71-9912-be57534ecc78
ms.openlocfilehash: f769de7bcf3e410cca717c17237d1e49ef8562c9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293594"
---
# <a name="adding-tabs-to-a-tab-control"></a>Agregar pestañas a un control de pestaña

Después de crear el control de ficha ([CTabCtrl](../mfc/reference/ctabctrl-class.md)), agregar tantas pestañas como sea necesario.

### <a name="to-add-a-tab-item"></a>Para agregar un elemento de pestaña

1. Preparar una [TCITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtcitema) estructura.

1. Llame a [CTabCtrl:: InsertItem](../mfc/reference/ctabctrl-class.md#insertitem), pasando la estructura.

1. Repita los pasos 1 y 2 para los elementos de una ficha adicional.

Para obtener más información, consulte [creación de un Control de ficha](/windows/desktop/Controls/tab-controls) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
