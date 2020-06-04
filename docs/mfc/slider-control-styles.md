---
title: Estilos de control deslizante
ms.date: 11/04/2016
helpviewer_keywords:
- slider controls [MFC], styles
- CSliderCtrl class [MFC], styles
- styles [MFC], CSliderCtrl
- styles [MFC], slider controls
ms.assetid: 64c491fc-5af1-4f97-ae30-854071b3dc02
ms.openlocfilehash: c6765445552826b71cca278c1fbbc66e500cb75a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307406"
---
# <a name="slider-control-styles"></a>Estilos de control deslizante

Controles deslizantes ([CSliderCtrl](../mfc/reference/csliderctrl-class.md)) puede tener una orientación vertical u horizontal. Pueden tener marcas de graduación en cualquier lado, ambos o ninguno. También puede usarse para especificar un intervalo de valores consecutivos. Estas propiedades se controlan mediante el uso de estilos de control deslizante, que se especifican al crear el control deslizante.

Los estilos TBS_HORZ y TBS_VERT determinan la orientación del control deslizante. Si no especifica una orientación, el control deslizante está orientado horizontalmente.

El estilo TBS_AUTOTICKS crea un control deslizante que tiene una marca de graduación por cada incremento en el intervalo de valores. Estas marcas de graduación se agregan automáticamente cuando se llama a la [SetRange](../mfc/reference/csliderctrl-class.md#setrange) función miembro. Si no especifica TBS_AUTOTICKS, puede usar las funciones miembro, como [SetTic](../mfc/reference/csliderctrl-class.md#settic) y [SetTicFreq](../mfc/reference/csliderctrl-class.md#setticfreq), para especificar las posiciones de las marcas de graduación. Para crear un control deslizante que no muestra las marcas de graduación, puede usar el estilo TBS_NOTICKS.

Puede mostrar las marcas de graduación en uno o ambos lados del control deslizante. Para los controles del control deslizante horizontal, puede especificar el estilo TBS_BOTTOM o TBS_TOP. Para los controles del control deslizante vertical, puede especificar el estilo TBS_BOTTOM o TBS_TOP. (TBS_BOTTOM y TBS_RIGHT son la configuración predeterminada). Para las marcas de graduación en ambos lados del control deslizante en cualquier orientación, especifique el estilo TBS_BOTH.

Un control deslizante puede mostrar un intervalo de selección solo si especifica el estilo TBS_ENABLESELRANGE al crearla. Cuando un control deslizante tiene este estilo, las marcas de graduación en las posiciones inicial y finales de un intervalo de selección se muestran como triángulos (en lugar de verticales guiones) y se resalta el intervalo de selección. Por ejemplo, los intervalos de selección podrían ser útiles en una aplicación de programación simple. El usuario podría seleccionar un intervalo de marcas de graduación correspondiente a las horas de un día para identificar una hora programada.

De forma predeterminada, la duración de deslizante un control deslizante del control varía cuando cambia el intervalo de selección. Si el control deslizante tiene el estilo TBS_FIXEDLENGTH, la longitud del control deslizante permanece igual incluso si cambia el intervalo de selección. Un control deslizante que el estilo TBS_NOTHUMB no incluye un control deslizante.

## <a name="see-also"></a>Vea también

[Uso de CSliderCtrl](../mfc/using-csliderctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
