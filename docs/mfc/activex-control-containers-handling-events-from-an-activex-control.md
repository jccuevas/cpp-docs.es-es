---
title: "Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "contenedores de controles ActiveX [C++], receptores de eventos"
  - "controles ActiveX [C++], eventos"
  - "BEGIN_EVENTSINK_MAP (macro)"
  - "END_EVENTSINK_MAP (macro), utilizar"
  - "controladores de eventos [C++], controles ActiveX"
  - "control de eventos [C++], controles ActiveX"
  - "eventos [C++], controles ActiveX"
  - "ON_EVENT (macro)"
ms.assetid: f9c106db-052f-4e32-82ad-750646aa760b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe mediante la ventana Propiedades para instalar controladores de eventos para controles ActiveX en un contenedor de controles ActiveX.  Se utilizan los controladores de eventos para recibir notificaciones \(del control\) de ciertos eventos y realizar alguna acción en respuesta.  Esta notificación se denomina la “despedida” el evento.  
  
> [!NOTE]
>  Este artículo utiliza un contenedor diálogo\- basado en proyecto denominado de contenedor de controles ActiveX y un control incrustado denominados Circ como ejemplos en los procedimientos y el código.  
  
 Mediante el botón eventos en la ventana Propiedades, puede crear un mapa de los eventos que pueden aparecer en la aplicación contenedora de controles ActiveX.  Este mapa, denominado “mapa de receptor de eventos,” crea y mantiene por Visual C\+\+ cuando agregue controladores de eventos a la clase del contenedor del control.  Cada controlador de eventos, implementado con un evento asigna entrada, asigna un evento específico de una función miembro del controlador de eventos del contenedor.  Esta función se denomina de controlador de eventos al evento especificado es desencadenado por el objeto de control ActiveX.  
  
 Para obtener más información sobre asignaciones de receptor de eventos, vea [Mapas de receptor de eventos](../mfc/reference/event-sink-maps.md) en *la referencia de la biblioteca de clases*.  
  
##  <a name="_core_event_handler_modifications_to_the_project"></a> Controlador de eventos Modifications al proyecto  
 Cuando se utiliza la ventana Propiedades para agregar controladores de eventos, un mapa de receptor de eventos se declara y se define en el proyecto.  Las instrucciones siguientes se agregan al archivo de control .CPP la primera vez que agrega un controlador de eventos.  Este código declara un receptor de eventos asignado para la clase de cuadro de diálogo \(en este caso, `CContainerDlg`\):  
  
 [!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]  
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]  
  
 Cuando utiliza la ventana Propiedades para agregar eventos, un evento asigna la entrada \(`ON_EVENT`\) se agrega al mapa de receptor de eventos y una función de controlador de eventos se agrega al archivo de implementación de contenedor \(.CPP\).  
  
 El ejemplo siguiente declara un controlador de eventos, denominado `OnClickInCircCtrl`, para el evento de **ClickIn** de control de Circ:  
  
 [!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]  
  
 Además, la plantilla siguiente se agrega al archivo de implementación de la clase de `CContainerDlg` \(.CPP\) para la función miembro de controlador de eventos:  
  
 [!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/CPP/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]  
  
 Para obtener más información acerca de las macros de receptor de eventos, vea [Mapas de receptor de eventos](../mfc/reference/event-sink-maps.md) en *la referencia de la biblioteca de clases*.  
  
#### Para crear una función de controlador de eventos  
  
1.  En la vista de clases, seleccione la clase de diálogo que contiene el control ActiveX.  Para este ejemplo, utilice `CContainerDlg`.  
  
2.  En la ventana Propiedades, haga clic en el botón **Eventos**.  
  
3.  En la ventana Propiedades, seleccione el identificador de control ActiveX incrustado.  Para este ejemplo, utilice `IDC_CIRCCTRL1`.  
  
     La ventana Propiedades muestra una lista de los eventos que se pueden desencadenar el control ActiveX incrustado.  Cualquier función miembro mostrada en negrita ya tiene funciones controladoras asignadas a él.  
  
4.  Seleccione el evento que desea que la clase de diálogo para controlar.  Para este ejemplo, seleccione **Hacer clic en**.  
  
5.  En el cuadro de lista desplegable a la derecha, seleccione **\<Add\> ClickCircctrl1**.  
  
6.  Haga doble clic en la nueva función de controlador de vista de la clase para saltar al código de controlador de eventos en el archivo de implementación \(.CPP\) de `CContainerDlg`.  
  
## Vea también  
 [Contenedores de controles ActiveX](../mfc/activex-control-containers.md)