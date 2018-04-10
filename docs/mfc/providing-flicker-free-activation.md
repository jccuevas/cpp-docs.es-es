---
title: Proporcionar activación sin parpadeo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], flicker-free
- flicker, MFC ActiveX controls
- activation [MFC], flicker-free
ms.assetid: bcb24b77-31d8-44a0-8c58-2ea6213b4c43
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1f14998ce663e5a8e53901acf9192719fa41e724
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="providing-flicker-free-activation"></a>Proporcionar activación sin parpadeo
Si el control se dibuja de forma idéntica en los Estados inactivos y activos (y no utiliza activación sin ventana), puede eliminar las operaciones de dibujo y el parpadeo visual que normalmente se producen al realizar la transición entre el inactiva Estados y activo. Para hacerlo, incluya el **noFlickerActivate** marca en el conjunto de indicadores devuelto por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags). Por ejemplo:  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-flicker-free-activation_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#13](../mfc/codesnippet/cpp/providing-flicker-free-activation_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-flicker-free-activation_3.cpp)]  
  
 El código para incluir este indicador se genera automáticamente si selecciona la **activación sin parpadeo** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página al crear el control con el Asistente para controles de ActiveX de MFC.  
  
 Si usas la activación sin ventana, esta optimización no tiene ningún efecto.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

