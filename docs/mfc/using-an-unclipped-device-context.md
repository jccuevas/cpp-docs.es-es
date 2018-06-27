---
title: Usar un contexto de dispositivo no recortado | Documentos de Microsoft
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
ms.openlocfilehash: 6d4fcfbe8e8e7eb174f85ced03bec822b4968bde
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954340"
---
# <a name="using-an-unclipped-device-context"></a>Usar un contexto de dispositivo no recortado
Si se está completamente seguro de que el control no se dibuje fuera su rectángulo de cliente, puede conseguir un aumento de velocidad pequeño pero detectables deshabilitando la llamada a `IntersectClipRect` que se realiza por `COleControl`. Para ello, quite el *clipPaintDC* marca desde el conjunto de indicadores devuelto por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/using-an-unclipped-device-context_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#14](../mfc/codesnippet/cpp/using-an-unclipped-device-context_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/using-an-unclipped-device-context_3.cpp)]  
  
 El código para quitar este indicador se genera automáticamente si selecciona la **contexto de dispositivo no recortado** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página, al crear el control con el Asistente para controles de ActiveX de MFC.  
  
 Si usas la activación sin ventana, esta optimización no tiene ningún efecto.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

