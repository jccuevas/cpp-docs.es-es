---
title: Estilos de Control deslizante | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f76fbe9f85d978a5c2865b48720588b620508a07
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951057"
---
# <a name="slider-control-styles"></a>Estilos de control deslizante
Controles deslizantes ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) puede tener una orientación vertical u horizontal. Pueden tener las marcas de graduación en cualquier lado, ambos o ninguno. Pueden usarse para especificar un intervalo de valores consecutivos. Estas propiedades se controlan mediante el uso de los estilos de control deslizante, que se especifican cuando se crea el control deslizante.  
  
 Los estilos TBS_HORZ y TBS_VERT determinan la orientación del control deslizante. Si no especifica una orientación, el control deslizante se orienta horizontalmente.  
  
 El estilo TBS_AUTOTICKS crea un control deslizante que tiene una marca de graduación para cada incremento en su intervalo de valores. Estas marcas de graduación se agregan automáticamente cuando se llama a la [SetRange](../mfc/reference/csliderctrl-class.md#setrange) función miembro. Si no se especifica TBS_AUTOTICKS, puede usar funciones de miembro, como [SetTic](../mfc/reference/csliderctrl-class.md#settic) y [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), para especificar las posiciones de las marcas de graduación. Para crear un control deslizante que no se muestran las marcas de graduación, puede usar el estilo TBS_NOTICKS.  
  
 Puede mostrar las marcas de graduación en uno o ambos lados del control deslizante. Para los controles de control deslizante horizontal, puede especificar el estilo TBS_BOTTOM o el estilo TBS_TOP. Para los controles de control deslizante vertical, puede especificar el estilo TBS_BOTTOM o TBS_TOP. (TBS_BOTTOM y TBS_RIGHT son la configuración predeterminada). Para las marcas de graduación en ambos lados del control deslizante en cualquier orientación, especifique el estilo TBS_BOTH.  
  
 Un control deslizante puede mostrar un intervalo de selección únicamente si se especifica el estilo TBS_ENABLESELRANGE al crearlo. Cuando un control deslizante tiene este estilo, las marcas de graduación en las posiciones inicial y finales de un intervalo de selección se muestran como triángulos (en lugar de guiones verticales) y se resalta el intervalo de selección. Por ejemplo, los intervalos de selección pueden ser útiles en una aplicación de programación simple. El usuario puede seleccionar un intervalo de marcas de graduación correspondiente a las horas en un día para identificar una hora de reunión programada.  
  
 De forma predeterminada, la longitud del control deslizante del control deslizante varía a medida que los cambios del intervalo de selección. Si el control deslizante tiene el estilo TBS_FIXEDLENGTH, la longitud del control deslizante sigue siendo el mismo incluso si cambia el intervalo de selección. Un control deslizante que tiene el estilo TBS_NOTHUMB no incluye un control deslizante.  
  
## <a name="see-also"></a>Vea también  
 [Usar CSliderCtrl](../mfc/using-csliderctrl.md)   
 [Controles](../mfc/controls-mfc.md)

