---
title: 'Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX'
ms.date: 09/12/2018
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
ms.openlocfilehash: 7487792fbc9fe6775640f40755a7f725543fb9f3
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907771"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX

En este artículo se describe el uso de la ventana **propiedades** (en **vista de clases**) para instalar controladores de eventos para controles ActiveX en un contenedor de controles ActiveX. Los controladores de eventos se utilizan para recibir notificaciones (del control) de determinados eventos y realizar alguna acción en respuesta. Esta notificación se denomina "activación" del evento.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

> [!NOTE]
>  En este artículo se usa un proyecto de contenedor de controles ActiveX basado en cuadros de diálogo denominado contenedor y un control incrustado denominado Circ como ejemplos en los procedimientos y el código.

Mediante el botón eventos de la ventana **propiedades** (en **vista de clases**), puede crear un mapa de eventos que se pueden producir en la aplicación contenedora de controles ActiveX. Este mapa, denominado "mapa de receptores de eventos", se crea y se mantiene mediante C++ visual al agregar controladores de eventos a la clase de contenedor de control. Cada controlador de eventos, implementado con una entrada de mapa de eventos, asigna un evento concreto a una función miembro del controlador de eventos de contenedor. Se llama a esta función de controlador de eventos cuando el objeto de control ActiveX activa el evento especificado.

Para obtener más información sobre las asignaciones de receptores de eventos, vea [asignaciones de receptores de eventos](../mfc/reference/event-sink-maps.md) en la referencia de la biblioteca de *clases*.

##  <a name="_core_event_handler_modifications_to_the_project"></a>Modificaciones del controlador de eventos en el proyecto

Cuando se usa la ventana **propiedades** para agregar controladores de eventos, se declara y se define un mapa de receptores de eventos en el proyecto. Las instrucciones siguientes se agregan al control. Archivo CPP la primera vez que se agrega un controlador de eventos. Este código declara una asignación de receptor de eventos para la clase de cuadro de diálogo (en `CContainerDlg`este caso,):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

A medida que se usa la ventana **propiedades** para agregar eventos, se agrega una`ON_EVENT`entrada de mapa de eventos () a la asignación de receptores de eventos y se agrega una función de controlador de eventos a la implementación del contenedor (. CPP).

En el ejemplo siguiente se declara un controlador de eventos `OnClickInCircCtrl`, denominado, para el evento `ClickIn` del control Circ:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Además, la plantilla siguiente se agrega a la implementación `CContainerDlg` de la clase (. CPP) para la función miembro del controlador de eventos:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Para obtener más información sobre las macros del receptor de eventos, vea [asignaciones de receptores de eventos](../mfc/reference/event-sink-maps.md) en la referencia de la biblioteca de *clases*.

#### <a name="to-create-an-event-handler-function"></a>Para crear una función de controlador de eventos

1. En Vista de clases, seleccione la clase de cuadro de diálogo que contiene el control ActiveX. En este ejemplo, use `CContainerDlg`.

1. En la ventana **Propiedades** , haga clic en el botón **Eventos** .

1. En la ventana **propiedades** , seleccione el ID. de control del control ActiveX incrustado. En este ejemplo, use `IDC_CIRCCTRL1`.

   La ventana **propiedades** muestra una lista de eventos que puede desencadenar el control ActiveX incrustado. Cualquier función miembro que se muestra en negrita ya tiene funciones controladoras asignadas.

1. Seleccione el evento que desea que controle la clase de cuadro de diálogo. En este ejemplo, seleccione **haga clic en**.

1. En el cuadro de lista desplegable de la derecha, seleccione  **\<agregar > ClickCircctrl1**.

1. Haga doble clic en la nueva función de controlador de Vista de clases para saltar al código del controlador de eventos en la implementación (. CPP) de `CContainerDlg`.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
