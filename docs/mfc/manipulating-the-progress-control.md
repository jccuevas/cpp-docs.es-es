---
title: Manipular el control de progreso
ms.date: 11/04/2016
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
ms.openlocfilehash: c9da6f8048adf1c7da184570ff7f94deee7441e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279195"
---
# <a name="manipulating-the-progress-control"></a>Manipular el control de progreso

Hay tres maneras de cambiar la posición actual de un control de progreso ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).

- La posición se puede cambiar por una cantidad de incremento predefinidos.

- La posición se puede cambiar mediante una cantidad arbitraria.

- La posición se puede cambiar a un valor específico.

### <a name="to-change-the-position-by-a-preset-amount"></a>Para cambiar la posición en un valor preestablecido

1. Use la [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) función miembro para establecer la cantidad de incremento. De forma predeterminada, este valor es 10. Este valor se establece normalmente como uno de los valores iniciales para el control. El valor de incremento puede ser negativo.

1. Use la [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) función miembro se incrementa la posición. Esto hace que el control de actualizarse a sí mismo.

    > [!NOTE]
    >  `StepIt` hará que la posición se ajuste. Por ejemplo, dado un intervalo de 1 -100, un paso de 20 y una posición de 90, `StepIt` establecerá la posición a 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Para cambiar la posición mediante una cantidad arbitraria

1. Use la [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) función miembro para cambiar la posición. `OffsetPos` Acepte los valores negativos.

    > [!NOTE]
    >  `OffsetPos`, a diferencia de `StepIt`, no se ajustará la posición. La nueva posición se ajusta para permanecer dentro del intervalo.

### <a name="to-change-the-position-to-a-specific-value"></a>Para cambiar la posición en un valor específico

1. Use la [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) función miembro para establecer la posición en un valor específico. Si es necesario, la nueva posición se ajusta para que esté dentro del intervalo.

Normalmente, el control de progreso se utiliza únicamente para la salida. Para obtener la posición actual sin especificar un valor nuevo, use [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Vea también

[Uso de CProgressCtrl](../mfc/using-cprogressctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
