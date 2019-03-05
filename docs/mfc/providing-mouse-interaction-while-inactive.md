---
title: Proporcionar interacción con el mouse mientras está inactivo
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], mouse interaction
ms.assetid: b09106bf-44c7-4b9b-a6d9-0d624f16f5b3
ms.openlocfilehash: d37deeec06551ae8bf340c99a9759327ce2ec2b7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57287848"
---
# <a name="providing-mouse-interaction-while-inactive"></a>Proporcionar interacción con el mouse mientras está inactivo

Si el control no se activa inmediatamente, es posible que aún desea proceso WM_SETCURSOR y mensajes WM_MOUSEMOVE, incluso si el control no tiene ninguna ventana propia. Esto puede realizarse habilitando `COleControl`de implementación de la `IPointerInactive` interfaz, que está deshabilitada de forma predeterminada. (Consulte la *ActiveX SDK* para obtener una descripción de esta interfaz.) Para habilitarla, incluya el indicador pointerInactive en el conjunto de indicadores devueltos por [COleControl:: GetControlFlags](../mfc/reference/colecontrol-class.md#getcontrolflags):

[!code-cpp[NVC_MFC_AxOpt#5](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_1.cpp)]
[!code-cpp[NVC_MFC_AxOpt#10](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_2.cpp)]
[!code-cpp[NVC_MFC_AxOpt#7](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_3.cpp)]

El código para incluir esta marca se genera automáticamente si selecciona la **Mouse puntero notificaciones cuando está inactivo** opción el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página al crear el control con el **Asistente para controles ActiveX MFC**.

Cuando el `IPointerInactive` interfaz está habilitada, el contenedor delega los mensajes WM_SETCURSOR y WM_MOUSEMOVE a él. `COleControl`de implementación de `IPointerInactive` envía los mensajes a través de mapas de mensajes de control después de ajustar el mouse coordina adecuadamente. Puede procesar los mensajes al igual que los mensajes de ventana normal mediante la adición de las entradas correspondientes en el mapa de mensajes. En los controladores para estos mensajes, evite usar el *m_hWnd* variable miembro (o cualquier función miembro que lo utiliza) sin antes comprobar que su valor no es **NULL**.

También es posible que desee un control inactivo a ser el destino de una operación de arrastrar y colocar OLE. Esto requiere la activación del control en el momento en que el usuario arrastra un objeto encima de él, para que la ventana del control se puede registrar como un destino de colocación. Para hacer que la activación se producen durante un arrastre, invalidar [COleControl:: GetActivationPolicy](../mfc/reference/colecontrol-class.md#getactivationpolicy)y devolver la marca POINTERINACTIVE_ACTIVATEONDRAG:

[!code-cpp[NVC_MFC_AxOpt#11](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_4.cpp)]

Habilitar la `IPointerInactive` interfaz significa normalmente que desea que el control sea capaz de procesar mensajes del mouse en todo momento. Para obtener este comportamiento en un contenedor que no es compatible con la `IPointerInactive` interfaz, debe tener el control siempre activado cuando está visible, lo que significa que el control debe incluir el indicador OLEMISC_ACTIVATEWHENVISIBLE entre sus indicadores varios. Sin embargo, para evitar que esta marca de surtan efecto en un contenedor que es compatible con `IPointerInactive`, también puede especificar el indicador OLEMISC_IGNOREACTIVATEWHENVISIBLE:

[!code-cpp[NVC_MFC_AxOpt#12](../mfc/codesnippet/cpp/providing-mouse-interaction-while-inactive_5.cpp)]

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)
