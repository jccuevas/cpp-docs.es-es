---
title: Optimizar el dibujo de controles
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 17cb7318e667fe4e16416d51e7e7fba02553cfe6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621018"
---
# <a name="optimizing-control-drawing"></a>Optimizar el dibujo de controles

Cuando se indica a un control que se dibuje en un contexto de dispositivo proporcionado por el contenedor, normalmente selecciona objetos GDI (como lápices, pinceles y fuentes) en el contexto del dispositivo, realiza sus operaciones de dibujo y restaura los objetos GDI anteriores. Si el contenedor tiene varios controles que se van a dibujar en el mismo contexto de dispositivo y cada control selecciona los objetos GDI que requiere, se puede guardar la hora si los controles no restauran individualmente los objetos seleccionados anteriormente. Una vez que se han dibujado todos los controles, el contenedor puede restaurar automáticamente los objetos originales.

Para detectar si un contenedor admite esta técnica, un control puede llamar a la función miembro [COleControl:: IsOptimizedDraw](reference/colecontrol-class.md#isoptimizeddraw) . Si esta función devuelve **true**, el control puede omitir el paso normal de restaurar los objetos previamente seleccionados.

Considere un control que tiene la siguiente función (no optimizada) `OnDraw` :

[!code-cpp[NVC_MFC_AxOpt#15](codesnippet/cpp/optimizing-control-drawing_1.cpp)]

El lápiz y el pincel de este ejemplo son variables locales, lo que significa que se llamará a los destructores cuando salgan del ámbito (cuando `OnDraw` finalice la función). Los destructores intentarán eliminar los objetos GDI correspondientes. Pero no se deben eliminar si tiene previsto dejarlos seleccionados en el contexto del dispositivo al volver de `OnDraw` .

Para evitar que los objetos [CPen (](reference/cpen-class.md) y [CBrush (](reference/cbrush-class.md) se destruyan cuando `OnDraw` finalice, almacénelos en variables de miembro en lugar de variables locales. En la declaración de clase del control, agregue declaraciones para dos nuevas variables de miembro:

[!code-cpp[NVC_MFC_AxOpt#16](codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](codesnippet/cpp/optimizing-control-drawing_3.h)]

A continuación, la `OnDraw` función se puede volver a escribir de la siguiente manera:

[!code-cpp[NVC_MFC_AxOpt#18](codesnippet/cpp/optimizing-control-drawing_4.cpp)]

Este enfoque evita la creación del lápiz y del pincel cada vez que `OnDraw` se llama a. La mejora de la velocidad se produce a costa de mantener datos de instancia adicionales.

Si cambia la propiedad ForeColor o BackColor, es necesario volver a crear el lápiz o el pincel. Para ello, invalide las funciones miembro [OnForeColorChanged](reference/colecontrol-class.md#onforecolorchanged) y [OnBackColorChanged](reference/colecontrol-class.md#onbackcolorchanged) :

[!code-cpp[NVC_MFC_AxOpt#19](codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Por último, para eliminar las llamadas innecesarias `SelectObject` , modifique `OnDraw` como se indica a continuación:

[!code-cpp[NVC_MFC_AxOpt#20](codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC: Optimización](mfc-activex-controls-optimization.md)<br/>
[COleControl (clase)](reference/colecontrol-class.md)<br/>
[Controles ActiveX MFC](mfc-activex-controls.md)<br/>
[Asistente para controles ActiveX MFC](reference/mfc-activex-control-wizard.md)<br/>
[Controles ActiveX MFC: Pintar un control ActiveX](mfc-activex-controls-painting-an-activex-control.md)
