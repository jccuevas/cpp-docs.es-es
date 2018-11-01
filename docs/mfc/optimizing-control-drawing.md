---
title: Optimizar el dibujo de controles
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 9096c43088c89ceef9e57d0e3a994340f9115d6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487352"
---
# <a name="optimizing-control-drawing"></a>Optimizar el dibujo de controles

Cuando un control se indica a dibujarse a sí mismo en un contexto de dispositivo proporcionado por el contenedor, lo normalmente selecciona objetos GDI (por ejemplo, lápices, pinceles y fuentes) en el contexto de dispositivo, realiza sus operaciones de dibujos y restaura los objetos GDI anteriores. Si el contenedor tiene varios controles que se va a dibujar en el mismo contexto de dispositivo, y cada control selecciona los objetos GDI que necesita, se puede guardar tiempo si los controles no restaurar individualmente los objetos previamente seleccionados. Después de han dibujado todos los controles, el contenedor puede restaurar automáticamente los objetos originales.

Para detectar si un contenedor es compatible con esta técnica, puede llamar un control de la [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) función miembro. Si esta función devuelve **TRUE**, el control puede omitir el paso normal de la restauración de los objetos previamente seleccionados.

Considere la posibilidad de un control que tiene las siguientes (sin optimizar) `OnDraw` función:

[!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]

El lápiz y el pincel en este ejemplo son variables locales, lo que significa que se llamará a los destructores cuando salen del ámbito (cuando el `OnDraw` función extremos). Los destructores intentarán eliminar los correspondientes objetos GDI. Pero no se elimina si va a dejar seleccionado en el contexto de dispositivo al volver de `OnDraw`.

Para evitar la [CPen](../mfc/reference/cpen-class.md) y [CBrush](../mfc/reference/cbrush-class.md) objetos desde que se está destruyendo cuando `OnDraw` finaliza, almacenarlos en variables de miembro en lugar de las variables locales. En la declaración de clase del control, agregue las declaraciones de dos nuevas variables de miembro:

[!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]

A continuación, la `OnDraw` función se puede reescribir del siguiente modo:

[!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]

Este enfoque evita la creación del lápiz y el pincel cada vez `OnDraw` se llama. Incluye la mejora de la velocidad a costa de mantener los datos de instancia adicional.

Si cambia la propiedad color de primer plano o el color de fondo, debe volver a crear el lápiz o un pincel. Para ello, invalide el [funciones miembro OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) y [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) funciones miembro:

[!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]

Por último, para eliminar innecesarios `SelectObject` modificar las llamadas, `OnDraw` como sigue:

[!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)<br/>
[COleControl (clase)](../mfc/reference/colecontrol-class.md)<br/>
[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)<br/>
[Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)<br/>
[Controles ActiveX MFC: Pintar un control ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)

