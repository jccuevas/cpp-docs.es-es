---
title: Usar controles deslizantes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CSliderCtrl class [MFC], using
- slider controls
- slider controls [MFC], using
ms.assetid: 2b1a8ac8-2b17-41e1-aa24-83c1fd737049
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fdab6a7fae25845da81ee7263e045e50951f557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-slider-controls"></a>Usar controles deslizantes
Uso típico de un control deslizante sigue el modelo siguiente:  
  
-   Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo, la creación es automática cuando se crea el cuadro de diálogo. (Debe tener un [CSliderCtrl](../mfc/reference/csliderctrl-class.md) miembro en la clase de cuadro de diálogo que se corresponde con el control deslizante.) Como alternativa, puede usar el [crear](../mfc/reference/csliderctrl-class.md#create) función de miembro para crear el control como una ventana secundaria de cualquier ventana.  
  
-   Llame a las distintas funciones de miembro Set para establecer valores para el control. Cambios que puede realizar incluyen establecer las posiciones mínimas y máxima para el control deslizante, dibujar las marcas de graduación, establecer un intervalo de selección y volver a colocar el control deslizante. Para los controles en un cuadro de diálogo, es un buen momento para hacer esto en el cuadro de diálogo [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) función.  
  
-   Cuando el usuario interactúa con el control, enviará varios mensajes de notificación. Puede extraer el valor del control deslizante desde el control mediante una llamada a la [GetPos](../mfc/reference/csliderctrl-class.md#getpos) función miembro.  
  
-   Cuando haya terminado con el control, debe asegurarse de que se destruya correctamente. Si el control deslizante está en un cuadro de diálogo y el `CSliderCtrl` automáticamente se destruirá el objeto. Si no es así, debe asegurarse de que tanto el control y la `CSliderCtrl` objeto se han destruido correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

