---
title: 'Controles ActiveX MFC: Optimización | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c91f147637b53250f8d373af9950d6205c82d3e3
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355316"
---
# <a name="mfc-activex-controls-optimization"></a>Controles ActiveX MFC: Optimización
Este artículo explica técnicas que puede usar para optimizar los controles ActiveX para mejorar el rendimiento.  
  
 Los temas [al desactivar la opción Activar cuando Visible](../mfc/turning-off-the-activate-when-visible-option.md) y [proporcionar Mouse Interaction While Inactive](../mfc/providing-mouse-interaction-while-inactive.md) sobre los controles que no se crean una ventana hasta que se activen. El tema [proporcionar activación sin ventana](../mfc/providing-windowless-activation.md) trata sobre los controles que nunca crean una ventana, incluso cuando se activan.  
  
 Las ventanas tienen dos grandes inconvenientes para los objetos OLE: impiden que los objetos de sean transparentes o no rectangulares cuando están activas y agregan una importante sobrecarga a la creación de instancias y la presentación de controles. Por lo general, la creación de una ventana tiene 60 por ciento del tiempo de creación de un control. Con una única ventana compartida (normalmente del contenedor) y algún código de distribución, un control recibe los mismos servicios de ventana, generalmente sin una pérdida de rendimiento. Tener una ventana es principalmente una sobrecarga innecesaria para el objeto.  
  
 Algunas optimizaciones no necesariamente mejorar el rendimiento cuando el control se utiliza en determinados contenedores. Por ejemplo, contenedores lanzados antes de 1996 no admitía la activación sin ventana, para implementar esta característica no proporcionará una ventaja para los contenedores antiguos. No obstante, casi todos los contenedores admiten la persistencia, para optimizar el código del control persistencia probablemente mejorará su rendimiento en cualquier contenedor. Si el control está diseñado específicamente para su uso con un determinado tipo de contenedor, puede que desee investigar cuáles de estas optimizaciones es compatible con ese contenedor. En general, sin embargo, debería intente implementar como muchas de estas técnicas, como son aplicables a su control determinado para asegurarse de que el control realiza tan bien como posiblemente pueden en una amplia gama de contenedores.  
  
 Puede implementar muchas de estas optimizaciones a través de la [Asistente para controles ActiveX de MFC](../mfc/reference/mfc-activex-control-wizard.md), en la [configuración del Control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) página.  
  
### <a name="mfc-activex-control-wizard-ole-optimization-options"></a>Opciones de optimización de OLE de Asistente de Control ActiveX MFC  
  
|Configuración de control en el Asistente para controles de ActiveX de MFC|Acción|Más información|  
|-------------------------------------------------------|------------|----------------------|  
|**Activar cuando está visible** casilla de verificación|Clear|[Si se desactiva la activar cuando opción esté Visible](../mfc/turning-off-the-activate-when-visible-option.md)|  
|**Activación sin ventana** casilla de verificación|Seleccionar|[Proporcionar activación sin ventana](../mfc/providing-windowless-activation.md)|  
|**Contexto de dispositivo no recortado** casilla de verificación|Seleccionar|[Uso de un contexto de dispositivo no recortado](../mfc/using-an-unclipped-device-context.md)|  
|**Activación sin parpadeo** casilla de verificación|Seleccionar|[Proporcionar activación sin parpadeo](../mfc/providing-flicker-free-activation.md)|  
|**Mueva el mouse notificaciones con el puntero cuando esté inactivo** casilla de verificación|Seleccionar|[Proporcionar interacción con el mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md)|  
|**Código de dibujo optimizado** casilla de verificación|Seleccionar|[Optimización del dibujo de controles](../mfc/optimizing-control-drawing.md)|  
  
 Para obtener información detallada sobre las funciones miembro que implementan estas optimizaciones, vea [COleControl](../mfc/reference/colecontrol-class.md). Las funciones miembro aparecen clasificadas por uso, como [operaciones sin ventanas](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) y [funciones de control de puntero inactivo](http://msdn.microsoft.com/en-us/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df).  
  
 Para obtener más información, consulte:  
  
-   [Optimización de la persistencia y la inicialización](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [Proporcionar activación sin ventana](../mfc/providing-windowless-activation.md)  
  
-   [Si se desactiva la activar cuando opción esté Visible](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [Proporcionar interacción con el mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [Proporcionar activación sin parpadeo](../mfc/providing-flicker-free-activation.md)  
  
-   [Uso de un contexto de dispositivo no recortado](../mfc/using-an-unclipped-device-context.md)  
  
-   [Optimización del dibujo de controles](../mfc/optimizing-control-drawing.md)  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

