---
title: 'Controles ActiveX MFC: Optimización'
ms.date: 09/12/2018
helpviewer_keywords:
- MFC ActiveX controls [MFC], windowless
- flicker-free ActiveX controls
- MFC ActiveX controls [MFC], mouse interaction
- device contexts, unclipped for MFC ActiveX controls
- MFC ActiveX controls [MFC], optimizing
- performance, ActiveX controls
- optimization, ActiveX controls
- MFC ActiveX controls [MFC], flicker-free
- windowless MFC ActiveX controls
- MFC ActiveX controls [MFC], active/inactive state
- optimizing performance, ActiveX controls
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
ms.openlocfilehash: 08cbb5ab0ff9b8c165e549bc2b250daebc1ce177
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62186897"
---
# <a name="mfc-activex-controls-optimization"></a>Controles ActiveX MFC: Optimización

En este artículo se explica técnicas que puede usar para optimizar los controles ActiveX para mejorar el rendimiento.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Los temas [al desactivar la opción Activar cuando Visible](../mfc/turning-off-the-activate-when-visible-option.md) y [proporcionar Mouse interacción inactivo](../mfc/providing-mouse-interaction-while-inactive.md) sobre los controles que no se crean una ventana hasta que se activen. El tema [proporcionar activación sin ventana](../mfc/providing-windowless-activation.md) se describen los controles que nunca crean una ventana, incluso cuando se activan.

Windows tienen dos inconvenientes principales para los objetos de OLE: impiden que los objetos sean transparentes o no rectangulares cuando está activo y agregan una gran sobrecarga a la creación de instancias y la presentación de controles. Normalmente, la creación de una ventana toma 60 por ciento del tiempo de creación de un control. Con una sola ventana compartida (normalmente del contenedor) y algún código de distribución, un control recibe los mismos servicios de ventana, generalmente sin una pérdida de rendimiento. Disponer de una ventana es principalmente una sobrecarga innecesaria para el objeto.

Algunas optimizaciones no necesariamente mejorar el rendimiento cuando se utiliza el control en ciertos contenedores. Por ejemplo, los contenedores anteriores a 1996 no admitía la activación sin ventana, para implementar esta característica no proporcionará una ventaja en contenedores más antiguos. Sin embargo, casi todos los contenedores admiten la persistencia, para optimizar el código de control persistencia probablemente mejorará su rendimiento en cualquier contenedor. Si el control está diseñado específicamente para su uso con un determinado tipo de contenedor, es posible que desea investigar lo que estas optimizaciones es compatible con ese contenedor. En general, sin embargo, debe intentar implementar igual que muchas de estas técnicas, como son aplicables a su control específico para asegurarse de que el control se realiza tan bien como posiblemente en una amplia gama de contenedores.

Puede implementar muchas de estas optimizaciones a través de la [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md), en el [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página.

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Opciones de optimización OLE de MFC ActiveX Control Asistente

|Configuración del control en el Asistente para controles de ActiveX de MFC|Acción|Más información|
|-------------------------------------------------------|------------|----------------------|
|**Activar cuando esté visible** casilla de verificación|Clear|[Si se desactiva el cuándo activar opción Visible](../mfc/turning-off-the-activate-when-visible-option.md)|
|**Activación sin ventana** casilla de verificación|Seleccionar|[Proporcionar activación sin ventana](../mfc/providing-windowless-activation.md)|
|**Contexto de dispositivo no recortado** casilla de verificación|Seleccionar|[Uso de un contexto de dispositivo no recortado](../mfc/using-an-unclipped-device-context.md)|
|**Activación sin parpadeo** casilla de verificación|Seleccionar|[Proporcionar activación sin parpadeo](../mfc/providing-flicker-free-activation.md)|
|**Mueva el mouse cuando está inactivo de notificaciones del puntero** casilla de verificación|Seleccionar|[Proporcionar interacción con el mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md)|
|**Código de dibujo optimizado** casilla de verificación|Seleccionar|[Optimización del dibujo de controles](../mfc/optimizing-control-drawing.md)|

Para obtener información detallada acerca de las funciones miembro que implementan estas optimizaciones, vea [COleControl](../mfc/reference/colecontrol-class.md).

Para obtener más información, consulte:

- [Optimización de la persistencia y la inicialización](../mfc/optimizing-persistence-and-initialization.md)

- [Proporcionar activación sin ventana](../mfc/providing-windowless-activation.md)

- [Si se desactiva el cuándo activar opción Visible](../mfc/turning-off-the-activate-when-visible-option.md)

- [Proporcionar interacción con el mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md)

- [Proporcionar activación sin parpadeo](../mfc/providing-flicker-free-activation.md)

- [Uso de un contexto de dispositivo no recortado](../mfc/using-an-unclipped-device-context.md)

- [Optimización del dibujo de controles](../mfc/optimizing-control-drawing.md)

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
