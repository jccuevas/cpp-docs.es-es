---
title: Funciones de miembro de botón de número | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- spin button control, methods
- CSpinButtonCtrl class [MFC], methods
ms.assetid: a08a26fd-b803-4cbe-a509-395fa357d057
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 524863b816c62903cb610b57a6e3275bcdf6a3d6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="spin-button-member-functions"></a>Funciones miembro del botón de número
Hay varias funciones miembro disponibles para el control de número ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)). Use estas funciones para cambiar los siguientes atributos del botón de número.  
  
-   **Aceleración** puede ajustar la velocidad a la que cambia la posición cuando el usuario mantiene presionado el botón de flecha. Para trabajar con aceleración, utilice la [funciones miembro SetAccel](../mfc/reference/cspinbuttonctrl-class.md#setaccel) y [GetAccel](../mfc/reference/cspinbuttonctrl-class.md#getaccel) funciones miembro.  
  
-   **Base** puede cambiar la base (10 o 16) que se usa para mostrar la posición en el título de la ventana relacionada. Para trabajar con la base, utilice la [GetBase](../mfc/reference/cspinbuttonctrl-class.md#getbase) y [SetBase](../mfc/reference/cspinbuttonctrl-class.md#setbase) funciones miembro.  
  
-   **Colega ventana** puede establecer dinámicamente la ventana relacionada. Para consultar o cambiar qué control es la ventana relacionada, utilice la [funciones miembro GetBuddy](../mfc/reference/cspinbuttonctrl-class.md#getbuddy) y [SetBuddy](../mfc/reference/cspinbuttonctrl-class.md#setbuddy) funciones miembro.  
  
-   **Posición** puede consultar y cambiar la posición. Para trabajar directamente con la posición, utilice la [GetPos](../mfc/reference/cspinbuttonctrl-class.md#getpos) y [SetPos](../mfc/reference/cspinbuttonctrl-class.md#setpos) funciones miembro. Como puede haber cambiado el título del control relacionado (por ejemplo, en el caso de que el relacionado sea un control de edición), `GetPos` recupera el título actual y ajusta la posición de la forma apropiada.  
  
-   **Intervalo** puede cambiar las posiciones mínimas y máxima para el botón de número. De forma predeterminada, el máximo se establece en 0 y el mínimo se establece en 100. Puesto que el valor máximo predeterminado es menor que el valor mínimo predeterminado, las acciones de los botones de flecha es contraproducente. Por lo general, se establecerá el intervalo utilizando la [SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange) función miembro. Para consultar el uso de intervalo [GetRange](../mfc/reference/cspinbuttonctrl-class.md#getrange).  
  
## <a name="see-also"></a>Vea también  
 [Usar CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Controles](../mfc/controls-mfc.md)

