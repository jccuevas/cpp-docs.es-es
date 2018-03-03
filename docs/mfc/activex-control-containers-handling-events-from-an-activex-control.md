---
title: 'Contenedores de controles ActiveX: Controlar eventos desde un Control ActiveX | Documentos de Microsoft'
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
- event handlers [MFC], ActiveX controls
- ActiveX control containers [MFC], event sinks
- event handling [MFC], ActiveX controls
- ON_EVENT macro [MFC]
- ActiveX controls [MFC], events [MFC]
- END_EVENTSINK_MAP macro, using
- events [MFC], ActiveX controls
- BEGIN_EVENTSINK_MAP macro
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 84e1571f400297584e12a40dfd2bfcc3c0b525d2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX
Este artículo describe mediante la ventana Propiedades para instalar a controladores de eventos para controles ActiveX en un contenedor de controles ActiveX. Los controladores de eventos se utilizan para recibir notificaciones (desde el control) de ciertos eventos y realizar alguna acción en respuesta. Esta notificación se denomina "activar" el evento.  
  
> [!NOTE]
>  Este artículo utiliza un basada en cuadros de diálogo contenedor proyecto de control ActiveX denominado Container y un control incrustado denominado Circ como ejemplos en los procedimientos y el código.  
  
 Con el botón de eventos en la ventana Propiedades, puede crear un mapa de eventos que se pueden producir en su aplicación de contenedor de controles ActiveX. Este mapa, denominado un "mapa de receptores de eventos '', se crean y mantienen por Visual C++ cuando agregue controladores de eventos a la clase de contenedor de control. Cada controlador de eventos, que se implementa con una entrada de mapa de eventos, asigna un evento específico a una función de miembro de controlador de eventos de contenedor. Esta función de controlador de eventos se llama cuando se desencadena el evento especificado por el objeto de control ActiveX.  
  
 Para obtener más información sobre los mapas de receptor de eventos, vea [mapas de receptor de eventos](../mfc/reference/event-sink-maps.md) en el *Class Library Reference*.  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a>Modificaciones del controlador de eventos en el proyecto  
 Cuando utiliza la ventana Propiedades para agregar controladores de eventos, un mapa de receptores de eventos se declaran y se definen en el proyecto. Las instrucciones siguientes se agregan al control. Archivo CPP la primera vez que se agrega un controlador de eventos. Este código declara un mapa de receptores de eventos para la clase de cuadro de diálogo (en este caso, `CContainerDlg`):  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 Cuando use la ventana Propiedades para agregar eventos, un evento asignar entrada (`ON_EVENT`) se agrega a la asignación de receptor de eventos y un controlador de eventos se agrega la función a la implementación del contenedor (. Archivo CPP).  
  
 En el ejemplo siguiente se declara un controlador de eventos, denominado `OnClickInCircCtrl`, para el control Circ **ClickIn** eventos:  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 Además, se agrega la siguiente plantilla para el `CContainerDlg` la implementación de clase (. Archivo CPP) para la función de miembro de controlador de eventos:  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 Para obtener más información sobre las macros de receptor de eventos, vea [mapas de receptor de eventos](../mfc/reference/event-sink-maps.md) en el *Class Library Reference*.  
  
#### <a name="to-create-an-event-handler-function"></a>Para crear una función de controlador de eventos  
  
1.  En la vista de clases, seleccione la clase de cuadro de diálogo que contiene el control ActiveX. En este ejemplo, utilice `CContainerDlg`.  
  
2.  En la ventana Propiedades, haga clic en el **eventos** botón.  
  
3.  En la ventana Propiedades, seleccione el identificador del control del control ActiveX incrustado. En este ejemplo, utilice `IDC_CIRCCTRL1`.  
  
     La ventana Propiedades muestra una lista de eventos que puede ser activado por el control ActiveX incrustado. Cualquier función miembro mostrada en negrita ya tiene funciones controladoras asignadas a él.  
  
4.  Seleccione el evento que desea que la clase de cuadro de diálogo para administrar. En este ejemplo, seleccione **haga clic en**.  
  
5.  En el cuadro de lista desplegable de la derecha, seleccione  **\<Agregar > ClickCircctrl1**.  
  
6.  Haga doble clic en la nueva función de controlador de vista de clases para saltar al código del controlador de eventos en la implementación (. Archivo CPP) de `CContainerDlg`.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

