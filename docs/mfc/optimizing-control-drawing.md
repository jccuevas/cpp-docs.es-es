---
title: Optimizar el dibujo de Control | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b3e79a7b8e539198844c106a9c41408f04d69186
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="optimizing-control-drawing"></a>Optimizar el dibujo de controles
Cuando un control se indica a dibujarse a sí mismo en un contexto de dispositivo proporcionado por el contenedor, lo normalmente selecciona objetos GDI (por ejemplo, lápices, pinceles y fuentes) en el contexto de dispositivo, realiza sus operaciones de dibujo y restaura los objetos GDI anteriores. Si el contenedor tiene varios controles que se van a dibujar en el mismo contexto de dispositivo, y cada control selecciona los objetos GDI que necesita, tiempo puede guardarse si los controles no restaurar individualmente los objetos previamente seleccionados. Después de han dibujado todos los controles, el contenedor puede restaurar automáticamente los objetos originales.  
  
 Para detectar si un contenedor es compatible con esta técnica, puede llamar un control de la [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw) función miembro. Si esta función devuelve **TRUE**, el control puede omitir el paso habitual de restablecer los objetos previamente seleccionados.  
  
 Considere la posibilidad de un control que tiene las siguientes (sin optimizar) `OnDraw` función:  
  
 [!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]  
  
 El lápiz y el pincel en este ejemplo son variables locales, lo que significa que los destructores se llamará cuando salen del ámbito (cuando el `OnDraw` funcionar extremos). Los destructores intentará eliminar los correspondientes objetos GDI. Pero no puede eliminar si tiene previsto dejarlos seleccionados en el contexto de dispositivo al volver de `OnDraw`.  
  
 Para evitar la [CPen](../mfc/reference/cpen-class.md) y [CBrush](../mfc/reference/cbrush-class.md) objetos desde que se destruya cuando `OnDraw` finaliza, almacenarlos en variables de miembro en lugar de las variables locales. En la declaración de clase del control, agregue declaraciones para dos nuevas variables de miembro:  
  
 [!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]  
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]  
  
 A continuación, la `OnDraw` función se puede reescribir del siguiente modo:  
  
 [!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]  
  
 Este enfoque evita la creación de la pluma y pincel cada vez `OnDraw` se llama. La mejora de la velocidad a costa de mantener los datos de instancia adicional.  
  
 Si cambia la propiedad de color de primer plano o color de fondo, debe volver a crear el lápiz o pincel. Para ello, invalide el [funciones miembro OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged) y [OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged) funciones miembro:  
  
 [!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]  
  
 Por último, para eliminar innecesarios `SelectObject` modificar las llamadas, `OnDraw` como se indica a continuación:  
  
 [!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: optimización](../mfc/mfc-activex-controls-optimization.md)   
 [COleControl (clase)](../mfc/reference/colecontrol-class.md)   
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Controles ActiveX de MFC](../mfc/mfc-activex-controls.md)   
 [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md)   
 [Controles ActiveX MFC: Pintar un control ActiveX](../mfc/mfc-activex-controls-painting-an-activex-control.md)

