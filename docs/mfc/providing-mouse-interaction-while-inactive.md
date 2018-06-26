---
title: Proporcionar interacción con el mouse (ratón) mientras está inactivo | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c322493a0ee1aebd068ffe1fedb695445b6274aa
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929499"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Proporcionar interacción con el mouse mientras está inactivo
Si el control no se activa inmediatamente, aún puede a proceso WM_SETCURSOR y mensajes WM_MOUSEMOVE, incluso aunque el control no tiene ninguna ventana propia. Esto puede realizarse habilitando `COleControl`de implementación de la `IPointerInactive` interfaz, que está deshabilitada de forma predeterminada. (Consulte la *ActiveX SDK* para obtener una descripción de esta interfaz.) Para habilitarla, incluya el indicador pointerInactive en el conjunto de indicadores devuelto por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):  
  
 [!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]  
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]  
  
 El código para incluir este indicador se genera automáticamente si selecciona la **Mouse puntero notificaciones cuando está inactivo** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página al crear el control con el **Asistente para controles ActiveX MFC**.  
  
 Cuando el `IPointerInactive` interfaz está habilitada, el contenedor delega los mensajes WM_SETCURSOR y WM_MOUSEMOVE en ella. `COleControl`de implementación de `IPointerInactive` envía los mensajes a través de mapas de mensajes de control después de ajustar el mouse coordina adecuadamente. Puede procesar los mensajes como mensajes de ventana normal agregando las entradas correspondientes al mapa de mensajes. En los controladores para estos mensajes, evite utilizar el *m_hWnd* variable miembro (o cualquier función miembro que lo utilice) sin comprobar primero que su valor no es **NULL**.  
  
 También puede un control inactivo sea el destino de una operación de arrastrar y colocar OLE. Esto requiere la activación del control en el momento en que el usuario arrastra un objeto sobre él, por lo que la ventana del control se puede registrar como un destino de colocación. Para hacer que la activación para que tenga lugar durante un arrastre, invalidar [COleControl:: GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)y devolver la marca POINTERINACTIVE_ACTIVATEONDRAG:  
  
 [!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]  
  
 Habilitar la `IPointerInactive` interfaz normalmente significa que desea que el control sea capaz de procesar mensajes del mouse en todo momento. Para obtener este comportamiento en un contenedor que no es compatible con la `IPointerInactive` interfaz, debe tener el control siempre activado cuando está visible, lo que significa que el control debe incluir el indicador OLEMISC_ACTIVATEWHENVISIBLE entre sus indicadores varios. Sin embargo, para evitar que esta marca de surten efecto en un contenedor que es compatible con `IPointerInactive`, también puede especificar el indicador OLEMISC_IGNOREACTIVATEWHENVISIBLE:  
  
 [!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)

