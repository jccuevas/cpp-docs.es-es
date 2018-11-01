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
ms.openlocfilehash: 5deff0a50de813cc5faa43a86e591d3003a3c03e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50659633"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX

En este artículo se analiza el uso de la ventana Propiedades para instalar a controladores de eventos para controles ActiveX en un contenedor de controles ActiveX. Los controladores de eventos se utilizan para recibir notificaciones (desde el control) de ciertos eventos y realizar alguna acción en respuesta. Esta notificación se denomina "activar" el evento.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

> [!NOTE]
>  Este artículo usa un basada en el cuadro de diálogo ActiveX control contenedor proyecto denominado contenedor y un control incrustado denominado Circ como ejemplos en los procedimientos y código.

Con el botón de eventos en la ventana Propiedades, puede crear un mapa de eventos que se pueden producir en la aplicación de contenedor del control ActiveX. Este mapa, denominado un "mapa de receptores de eventos '', se crea y mantiene Visual C++ al agregar controladores de eventos a la clase contenedora del control. Cada controlador de eventos, que se implementa con una entrada de mapa, un evento específico asigna a una función de miembro de controlador de eventos de contenedor. Esta función de controlador de eventos se llama cuando se desencadena el evento especificado por el control ActiveX.

Para obtener más información sobre los mapas de receptor de eventos, consulte [mapas de receptor de eventos](../mfc/reference/event-sink-maps.md) en el *Class Library Reference*.

##  <a name="_core_event_handler_modifications_to_the_project"></a> Modificaciones de controlador de eventos en el proyecto

Cuando se usa la ventana Propiedades para agregar controladores de eventos, un mapa de receptores de eventos se declara y define en el proyecto. Las instrucciones siguientes se agregan al control. Archivo CPP la primera vez que se agrega un controlador de eventos. Este código declara un mapa de receptores de eventos para la clase de cuadro de diálogo (en este caso, `CContainerDlg`):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

Si usa la ventana Propiedades para agregar eventos, un evento asignar entrada (`ON_EVENT`) se agrega a la asignación de receptor de eventos y un controlador de eventos (función) se agrega a la implementación del contenedor (. Archivo CPP).

En el ejemplo siguiente se declara un controlador de eventos, llamado `OnClickInCircCtrl`, para el control Circ `ClickIn` eventos:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Además, la plantilla siguiente se agrega a la `CContainerDlg` implementación de la clase (. Archivo CPP) de la función miembro de controlador de eventos:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Para obtener más información sobre las macros de receptor de eventos, consulte [mapas de receptor de eventos](../mfc/reference/event-sink-maps.md) en el *Class Library Reference*.

#### <a name="to-create-an-event-handler-function"></a>Para crear una función de controlador de eventos

1. En la vista de clases, seleccione la clase de cuadro de diálogo que contiene el control ActiveX. En este ejemplo, utilice `CContainerDlg`.

1. En la ventana Propiedades, haga clic en el **eventos** botón.

1. En la ventana Propiedades, seleccione el identificador de control del control ActiveX incrustado. En este ejemplo, utilice `IDC_CIRCCTRL1`.

   La ventana Propiedades muestra una lista de eventos que pueden activar el control ActiveX incrustado. Cualquier función miembro que se muestra en negrita ya tiene funciones controladoras asignadas a ella.

1. Seleccione el evento que desee de la clase de cuadro de diálogo para administrar. En este ejemplo, seleccione **haga clic en**.

1. En el cuadro de lista desplegable de la derecha, seleccione  **\<Agregar > ClickCircctrl1**.

1. Haga doble clic en la nueva función de controlador de vista de clases para saltar al código del controlador de eventos en la implementación (. Archivo CPP) de `CContainerDlg`.

## <a name="see-also"></a>Vea también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)

