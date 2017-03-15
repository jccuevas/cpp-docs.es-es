---
title: "Controles ActiveX MFC: Optimizaci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contextos de dispositivo, no recortado de controles ActiveX"
  - "controles ActiveX sin parpadeo"
  - "controles ActiveX en MFC, estado activo e inactivo"
  - "controles ActiveX en MFC, sin parpadeo"
  - "controles ActiveX en MFC, interacción del mouse"
  - "controles ActiveX en MFC, optimizar"
  - "controles ActiveX en MFC, sin ventana"
  - "optimización, controles ActiveX"
  - "optimizar el rendimiento, controles ActiveX"
  - "rendimiento, controles ActiveX"
  - "controles ActiveX en MFC sin ventanas"
ms.assetid: 8b11f26a-190d-469b-b594-5336094a0109
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Controles ActiveX MFC: Optimizaci&#243;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica las técnicas que puede utilizar para optimizar los controles ActiveX para mejorar el rendimiento.  
  
 Los temas [Girar Off la opción visible de Activar Cuando](../mfc/turning-off-the-activate-when-visible-option.md) y [Proporcionar la interacción del mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md) tratan los controles que no crean una ventana hasta elevado.  El tema [Proporcionar la activación sin ventana](../mfc/providing-windowless-activation.md) explica los controles que nunca se crea una ventana, incluso cuando se producen.  
  
 Windows tiene dos desventajas importantes para los objetos OLE: impiden que los objetos sean transparentes o rectangular cuando el activo, y se agregan una sobrecarga grande al ámbito y la presentación de controles.  Normalmente, creando una ventana contiene el 60 por ciento de la hora de creación de un control.  Con una sola ventana compartida \(normalmente el contenedor\) y código que envía, un control recibe los mismos servicios de la ventana, normalmente sin una pérdida de rendimiento.  Tener una ventana es principalmente sobrecarga innecesaria para el objeto.  
  
 Algunas optimizaciones no mejoran necesariamente rendimiento cuando éste se utiliza en algunos contenedores.  Por ejemplo, los contenedores liberar antes de 1996 no admitidos activación sin ventana, por lo que implementar esta característica no proporcionará una ventaja en contenedores más antiguos.  Sin embargo, casi cada contenedor admite la persistencia, por lo que optimizar el código de persistencia de control mejorará probablemente su rendimiento en cualquier contenedor.  Si el control está diseñado específicamente para utilizarlo con un tipo determinado de contenedor, quizá desee investigar que de estas optimizaciones es compatible con ese contenedor.  Sin embargo, en general debe intentar implementar tanto de estas técnicas como aplicable al control determinado garantizar el control realice tan bien como puede posiblemente en una amplia gama de contenedores.  
  
 Puede implementar muchas de estas optimizaciones con [Asistente para controles ActiveX MFC](../mfc/reference/mfc-activex-control-wizard.md), en la página de [Configuración del control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) .  
  
### Opciones VIEJAS de optimización del asistente para controles ActiveX MFC  
  
|Valor del Control del asistente para controles ActiveX MFC|Acción|Más información|  
|----------------------------------------------------------------|------------|---------------------|  
|Casilla de**Activate when visible**|Clear|[Girar Off la opción visible de Activar Cuando](../mfc/turning-off-the-activate-when-visible-option.md)|  
|Casilla de**Windowless activation**|Seleccionar|[Proporcionar la activación sin ventana](../mfc/providing-windowless-activation.md)|  
|Casilla de**Unclipped device context**|Seleccionar|[Mediante un contexto de dispositivo de Unclipped](../mfc/using-an-unclipped-device-context.md)|  
|Casilla de**Flicker\-free activation**|Seleccionar|[Proporcionar la activación libre de centelleo](../mfc/providing-flicker-free-activation.md)|  
|Casilla de**Mouse pointer notifications when inactive**|Seleccionar|[Proporcionar la interacción del mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md)|  
|Casilla de**Optimized drawing code**|Seleccionar|[Optimizar el gráfico de Control](../mfc/optimizing-control-drawing.md)|  
  
 Para obtener información detallada sobre las funciones miembro que implementan estas optimizaciones, vea [COleControl](../mfc/reference/colecontrol-class.md).  Las funciones miembro son indicadas por el uso, como [Operaciones sin ventana](http://msdn.microsoft.com/es-es/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df) y [Puntero inactivo que administra funciones](http://msdn.microsoft.com/es-es/e9e28f79-9a70-4ae4-a5aa-b3e92f1904df).  
  
 Para obtener más información, vea:  
  
-   [Optimizar Persistence y la inicialización](../mfc/optimizing-persistence-and-initialization.md)  
  
-   [Proporcionar la activación sin ventana](../mfc/providing-windowless-activation.md)  
  
-   [Girar Off la opción visible de Activar Cuando](../mfc/turning-off-the-activate-when-visible-option.md)  
  
-   [Proporcionar la interacción del mouse mientras está inactivo](../mfc/providing-mouse-interaction-while-inactive.md)  
  
-   [Proporcionar la activación libre de centelleo](../mfc/providing-flicker-free-activation.md)  
  
-   [Mediante un contexto de dispositivo de Unclipped](../mfc/using-an-unclipped-device-context.md)  
  
-   [Optimizar el gráfico de Control](../mfc/optimizing-control-drawing.md)  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)