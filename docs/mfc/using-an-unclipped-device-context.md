---
title: Usar un contexto de dispositivo no recortado
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
ms.openlocfilehash: 0f129c0bfa5bd76df4ba34b117e7ed8aa08c2ecb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62411817"
---
# <a name="using-an-unclipped-device-context"></a>Usar un contexto de dispositivo no recortado

Si está completamente seguro de que el control no dibujar fuera de su rectángulo cliente, puede conseguir un aumento en velocidad pequeño pero detectable deshabilitando la llamada a `IntersectClipRect` que se realiza por `COleControl`. Para ello, quite el *clipPaintDC* marca del conjunto de marcas devueltas por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

El código para quitar este indicador se genera automáticamente si selecciona la **contexto de dispositivo no recortado** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página, al crear el control con el Asistente para controles de ActiveX de MFC.

Si usas la activación sin ventana, esta optimización no tiene ningún efecto.

## <a name="see-also"></a>Vea también

[Controles ActiveX de MFC: optimización](../mfc/mfc-activex-controls-optimization.md)
