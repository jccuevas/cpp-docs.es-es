---
title: "Si se desactiva la opción Activar cuando Visible | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], activate options
- Activate When Visible option [MFC]
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 25521d75921b377730a7f9afac71f2a60c055216
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="turning-off-the-activate-when-visible-option"></a>Desactivar la opción Activar cuando esté visible
Un control tiene dos estados básicos: activo e inactivo. Tradicionalmente, se distinguían por el hecho de que el control tuviera o no una ventana. Un control activo tenía una ventana; un control inactivo no la tenía. Con la introducción de la activación sin ventana, esta distinción ya no es universal, pero sigue aplicándose a muchos controles.  
  
 En comparación con el resto de la inicialización suelen ser realizada por un control ActiveX, la creación de una ventana es una operación muy costosa. Idealmente, un control debería posponer la creación de su ventana hasta que sea absolutamente necesario.  
  
 Muchos controles no es necesario que estén activas son visibles en un contenedor de todo el tiempo. A menudo, un control puede permanecer en el estado inactivo hasta que el usuario realiza una operación que requiere que se activen (por ejemplo, hacer clic con el mouse o presionar la tecla TAB). Para hacer que un control permanezca inactivo hasta que el contenedor necesite activarlo, quite el **OLEMISC_ACTIVATEWHENVISIBLE** indicador de indicadores varios del control:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/cpp/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 El **OLEMISC_ACTIVATEWHENVISIBLE** marca automáticamente se omite si desactiva la **activar cuando está Visible** opción en el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página de ActiveX de MFC Asistente para controles cuando se crea el control.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

