---
title: Manipular el Control de progreso | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CProgressCtrl class [MFC], working with
- progress controls [MFC], manipulating
- CProgressCtrl class [MFC], manipulating
- controlling progress controls [MFC]
- CProgressCtrl class [MFC], using
ms.assetid: 9af561d1-980b-4003-a6da-ff79be15bf23
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 415061306c5e743b9ed95ee5c7105133d2e4d340
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="manipulating-the-progress-control"></a>Manipular el control de progreso
Hay tres maneras de cambiar la posición actual de un control de progreso ([CProgressCtrl](../mfc/reference/cprogressctrl-class.md)).  
  
-   La posición se puede cambiar por una cantidad de incremento preestablecida.  
  
-   La posición se puede cambiar mediante una cantidad arbitraria.  
  
-   La posición puede cambiarse a un valor específico.  
  
### <a name="to-change-the-position-by-a-preset-amount"></a>Para cambiar la posición en un valor preestablecido  
  
1.  Use la [SetStep](../mfc/reference/cprogressctrl-class.md#setstep) función de miembro para establecer la cantidad de incremento. De forma predeterminada, este valor es 10. Este valor se establece normalmente como uno de los valores iniciales para el control. El valor de incremento puede ser negativo.  
  
2.  Use la [StepIt](../mfc/reference/cprogressctrl-class.md#stepit) función de miembro para incrementar la posición. Esto hace que vuelva a dibujarse el control.  
  
    > [!NOTE]
    >  `StepIt` hará que la posición que va a contener. Por ejemplo, dado un intervalo de 1 -100, un paso de 20 y una posición de 90, `StepIt` establecerá la posición a 10.  
  
### <a name="to-change-the-position-by-an-arbitrary-amount"></a>Para cambiar la posición mediante una cantidad arbitraria  
  
1.  Use la [OffsetPos](../mfc/reference/cprogressctrl-class.md#offsetpos) función de miembro para cambiar la posición. `OffsetPos` Acepte los valores negativos.  
  
    > [!NOTE]
    >  `OffsetPos`, a diferencia de `StepIt`, no se ajustará la posición. La nueva posición se ajusta para permanecer dentro del intervalo.  
  
### <a name="to-change-the-position-to-a-specific-value"></a>Para cambiar la posición en un valor específico  
  
1.  Use la [SetPos](../mfc/reference/cprogressctrl-class.md#setpos) función de miembro para establecer la posición en un valor específico. Si es necesario, la nueva posición se ajusta para estar dentro del intervalo.  
  
 Normalmente, el control de progreso se utiliza solamente para la salida. Para obtener la posición actual sin especificar un valor nuevo, use [GetPos](../mfc/reference/cprogressctrl-class.md#getpos).  
  
## <a name="see-also"></a>Vea también  
 [Usar CProgressCtrl](../mfc/using-cprogressctrl.md)   
 [Controles](../mfc/controls-mfc.md)

