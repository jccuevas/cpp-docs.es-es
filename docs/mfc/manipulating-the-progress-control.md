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
ms.openlocfilehash: 3e3521a82854a85062f9b06bc33eb268d4b9c7a6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622432"
---
# <a name="manipulating-the-progress-control"></a>Manipular el control de progreso

Hay tres maneras de cambiar la posición actual de un control de progreso ([CProgressCtrl](reference/cprogressctrl-class.md)).

- La posición se puede cambiar por una cantidad de incremento preestablecido.

- La posición se puede cambiar en una cantidad arbitraria.

- La posición se puede cambiar a un valor específico.

### <a name="to-change-the-position-by-a-preset-amount"></a>Para cambiar la posición en una cantidad preestablecida

1. Utilice la función miembro [SetStep](reference/cprogressctrl-class.md#setstep) para establecer la cantidad de incremento. De forma predeterminada, este valor es 10. Este valor se establece normalmente como uno de los valores iniciales del control. El valor del paso puede ser negativo.

1. Utilice la función miembro [StepIt](reference/cprogressctrl-class.md#stepit) para incrementar la posición. Esto hace que el control se vuelva a dibujar.

    > [!NOTE]
    >  `StepIt`hará que se ajuste la posición. Por ejemplo, dado un intervalo de 1 -100, un paso de 20 y una posición de 90, `StepIt` establecerá la posición en 10.

### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Para cambiar la posición en una cantidad arbitraria

1. Utilice la función miembro [OffsetPos](reference/cprogressctrl-class.md#offsetpos) para cambiar la posición. `OffsetPos`aceptará valores negativos.

    > [!NOTE]
    >  `OffsetPos`, a diferencia de `StepIt` , no ajustará la posición. La nueva posición se ajusta para permanecer dentro del intervalo.

### <a name="to-change-the-position-to-a-specific-value"></a>Para cambiar la posición a un valor específico

1. Utilice la función miembro [setPos](reference/cprogressctrl-class.md#setpos) para establecer la posición en un valor específico. Si es necesario, la nueva posición se ajusta para que esté dentro del intervalo.

Normalmente, el control de progreso se utiliza únicamente para la salida. Para obtener la posición actual sin especificar un nuevo valor, use [getPos](reference/cprogressctrl-class.md#getpos).

## <a name="see-also"></a>Consulte también

[Usar CProgressCtrl](using-cprogressctrl.md)<br/>
[Permite](controls-mfc.md)
