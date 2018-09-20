---
title: Usar un contexto de dispositivo no recortado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], unclipped device context
ms.assetid: 9c020063-73da-4803-bf7b-2e1fd950c9ed
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 479009865fe9fd226466059382456f403e90c18a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389595"
---
# <a name="using-an-unclipped-device-context"></a>Usar un contexto de dispositivo no recortado

Si está completamente seguro de que el control no dibujar fuera de su rectángulo cliente, puede conseguir un aumento en velocidad pequeño pero detectable deshabilitando la llamada a `IntersectClipRect` que se realiza por `COleControl`. Para ello, quite el *clipPaintDC* marca del conjunto de marcas devueltas por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]

El código para quitar este indicador se genera automáticamente si selecciona la **contexto de dispositivo no recortado** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página, al crear el control con el Asistente para controles de ActiveX de MFC.

Si usas la activación sin ventana, esta optimización no tiene ningún efecto.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

