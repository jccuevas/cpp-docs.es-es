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
ms.openlocfilehash: b4e12889ca1bb5f4bb423a1f1ede1c396f8d60b5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84615400"
---
# <a name="mfc-activex-controls-optimization"></a>Controles ActiveX MFC: Optimización

En este artículo se explican las técnicas que puede usar para optimizar los controles ActiveX para mejorar el rendimiento.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Los temas desactivando [la opción activar cuando esté visible](turning-off-the-activate-when-visible-option.md) y [proporcionando interacción con el mouse mientras están inactivas](providing-mouse-interaction-while-inactive.md) describen los controles que no crean una ventana hasta que se activan. El tema [proporcionar activación sin ventana](providing-windowless-activation.md) describe los controles que nunca crean una ventana, incluso cuando se activan.

Las ventanas tienen dos desventajas principales para los objetos OLE: impiden que los objetos sean transparentes o no rectangulares cuando están activos, y agregan una gran sobrecarga a la creación de instancias y la presentación de controles. Normalmente, la creación de una ventana tarda el 60 por ciento de la hora de creación de un control. Con una sola ventana compartida (normalmente la del contenedor) y algún código de distribución, un control recibe los mismos servicios de ventana, generalmente sin pérdida de rendimiento. Tener una ventana es principalmente una sobrecarga innecesaria para el objeto.

Algunas optimizaciones no mejoran el rendimiento cuando el control se usa en determinados contenedores. Por ejemplo, los contenedores que se publicaron antes de 1996 no eran compatibles con la activación sin ventanas, por lo que la implementación de esta característica no ofrecerá ninguna ventaja en los contenedores más antiguos. Sin embargo, casi todos los contenedores admiten la persistencia, por lo que es probable que la optimización del código de persistencia del control mejore su rendimiento en cualquier contenedor. Si el control está diseñado específicamente para usarse con un tipo de contenedor determinado, es posible que desee investigar cuál de estas optimizaciones es compatible con ese contenedor. Sin embargo, en general, debe intentar implementar tantas técnicas como sean aplicables a su control concreto para asegurarse de que el control se realiza así como en una amplia gama de contenedores.

Puede implementar muchas de estas optimizaciones mediante el [Asistente para controles ActiveX MFC](reference/mfc-activex-control-wizard.md), en la página [configuración del control](reference/control-settings-mfc-activex-control-wizard.md) .

### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Opciones de optimización OLE del Asistente para controles ActiveX MFC

|Configuración del control en el Asistente para controles ActiveX MFC|Acción|Más información|
|-------------------------------------------------------|------------|----------------------|
|Casilla **activar cuando esté visible**|Desactivar|[Desactivar la opción activar cuando esté visible](turning-off-the-activate-when-visible-option.md)|
|Casilla **activación sin ventana**|Seleccionar|[Proporcionar activación sin ventana](providing-windowless-activation.md)|
|Casilla **contexto de dispositivo no recortado**|Seleccionar|[Uso de un contexto de dispositivo no recortado](using-an-unclipped-device-context.md)|
|Casilla **de activación sin parpadeo**|Seleccionar|[Proporcionar activación sin parpadeo](providing-flicker-free-activation.md)|
|Casilla **notificaciones del puntero del mouse cuando está inactivo**|Seleccionar|[Proporcionar interacción con el mouse mientras está inactivo](providing-mouse-interaction-while-inactive.md)|
|Casilla de verificación **código de dibujo optimizado**|Seleccionar|[Optimizar el dibujo de controles](optimizing-control-drawing.md)|

Para obtener información detallada sobre las funciones miembro que implementan estas optimizaciones, vea [COleControl](reference/colecontrol-class.md).

Para obtener más información, consulte:

- [Optimizar la persistencia y la inicialización](optimizing-persistence-and-initialization.md)

- [Proporcionar activación sin ventana](providing-windowless-activation.md)

- [Desactivar la opción activar cuando esté visible](turning-off-the-activate-when-visible-option.md)

- [Proporcionar interacción con el mouse mientras está inactivo](providing-mouse-interaction-while-inactive.md)

- [Proporcionar activación sin parpadeo](providing-flicker-free-activation.md)

- [Uso de un contexto de dispositivo no recortado](using-an-unclipped-device-context.md)

- [Optimizar el dibujo de controles](optimizing-control-drawing.md)

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
