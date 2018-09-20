---
title: Usar controles deslizantes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d0496a15b289ec055fd2706975603f25cef13938
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46388841"
---
# <a name="using-slider-controls"></a>Usar controles deslizantes

Uso típico de un control deslizante sigue el patrón siguiente:

- Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo, creación es automática cuando se crea el cuadro de diálogo. (Debe tener un [CSliderCtrl](../mfc/reference/csliderctrl-class.md) miembro en la clase de cuadro de diálogo que se corresponde con el control deslizante.) Como alternativa, puede usar el [crear](../mfc/reference/csliderctrl-class.md#create) función miembro para crear el control como una ventana secundaria de cualquier ventana.

- Llamar a las distintas funciones de miembro Set para establecer valores para el control. Los cambios que puede realizar incluyen establecer las posiciones mínimas y máxima para el control deslizante, dibujar marcas de graduación, establecer un intervalo de selección y volver a colocar el control deslizante. Para los controles en un cuadro de diálogo, un buen momento para hacerlo es en el cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) función.

- Cuando el usuario interactúa con el control, enviará varios mensajes de notificación. Puede extraer el valor del control deslizante desde el control mediante una llamada a la [GetPos](../mfc/reference/csliderctrl-class.md#getpos) función miembro.

- Cuando haya terminado con el control, deberá asegurarse de que se destruya correctamente. Si el control deslizante está en un cuadro de diálogo y el `CSliderCtrl` automáticamente se destruirá el objeto. Si no, deberá asegurarse de que el control y la `CSliderCtrl` objeto se destruyan correctamente.

## <a name="see-also"></a>Vea también

[Uso de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

