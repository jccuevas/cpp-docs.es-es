---
title: Funciones miembro del botón de número
ms.date: 11/04/2016
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
ms.openlocfilehash: ffd07377d54fcfff93ab4ab3771515a90ccf2785
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50542602"
---
# <a name="spin-button-member-functions"></a>Funciones miembro del botón de número

Hay varias funciones de miembro para el control de número ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Utilice estas funciones para cambiar los siguientes atributos del botón de número.

- **Aceleración** puede ajustar la velocidad a la que la posición cambia cuando el usuario mantiene presionado el botón de flecha. Para trabajar con aceleración, utilice el [funciones miembro SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) y [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) funciones miembro.

- **Base** puede cambiar la base (10 o 16) utilizada para mostrar la posición del título de la ventana relacionada. Para trabajar con la base, use el [GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase) y [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) funciones miembro.

- **Aplazados ventana** puede establecer dinámicamente la ventana relacionada. Para consultar o cambiar qué control es la ventana relacionada, utilice el [funciones miembro GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) y [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) funciones miembro.

- **Posición** puede consultar y cambiar la posición. Para trabajar directamente con la posición, utilice el [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) y [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) funciones miembro. Como puede haber cambiado el título del control relacionado (por ejemplo, en el caso que el amigo es un control de edición), `GetPos` recupera el título y el ajusta la posición en consecuencia.

- **Intervalo** puede cambiar las posiciones mínimas y máxima para el botón de número. De forma predeterminada, el máximo se establece en 0 y el mínimo se establece en 100. Puesto que el valor máximo predeterminado es menor que el valor mínimo predeterminado, las acciones de los botones de flecha es intuitivo. Normalmente, establecerá el intervalo con el [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) función miembro. Para consultar el uso de intervalo [GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange).

## <a name="see-also"></a>Vea también

[Uso de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

