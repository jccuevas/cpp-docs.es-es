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
ms.openlocfilehash: ae623ee0973e78db3b542646dd6bdec58cc2dfc8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367949"
---
# <a name="activex-control-containers-handling-events-from-an-activex-control"></a>Contenedores de controles ActiveX: Controlar eventos desde un control ActiveX

En este artículo se describe el uso de la ventana **Propiedades** (en **la**vista de clases ) para instalar controladores de eventos para controles ActiveX en un contenedor de controles ActiveX. Los controladores de eventos se usan para recibir notificaciones (del control) de determinados eventos y realizar alguna acción en respuesta. Esta notificación se denomina "disparar" el evento.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

> [!NOTE]
> En este artículo se usa un proyecto de contenedor de control ActiveX basado en cuadros de diálogo denominado Container y un control incrustado denominado Circ como ejemplos en los procedimientos y el código.

Mediante el botón Eventos de la ventana **Propiedades** **(en**la vista de clases ), puede crear un mapa de eventos que pueden producirse en la aplicación contenedora de controles ActiveX. Visual C++ crea y mantiene este mapa, denominado "mapa de receptores de eventos,'' al agregar controladores de eventos a la clase contenedora de control. Cada controlador de eventos, implementado con una entrada de mapa de eventos, asigna un evento específico a una función miembro del controlador de eventos de contenedor. Se llama a esta función de controlador de eventos cuando el objeto de control ActiveX desencadena el evento especificado.

Para obtener más información sobre los mapas de receptores de eventos, consulte Mapas de [receptores](../mfc/reference/event-sink-maps.md) de eventos en la Referencia de la biblioteca de *clases*.

## <a name="event-handler-modifications-to-the-project"></a><a name="_core_event_handler_modifications_to_the_project"></a>Modificaciones del controlador de eventos en el proyecto

Cuando se usa la ventana **Propiedades** para agregar controladores de eventos, se declara y define un mapa de receptores de eventos en el proyecto. Las instrucciones siguientes se agregan al control . CPP la primera vez que se agrega un controlador de eventos. Este código declara un mapa de receptor de eventos `CContainerDlg`para la clase de cuadro de diálogo (en este caso, ):

[!code-cpp[NVC_MFC_AxCont#8](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_1.cpp)]
[!code-cpp[NVC_MFC_AxCont#9](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_2.cpp)]

A medida **Properties** que se usa la ventana Propiedades`ON_EVENT`para agregar eventos, se agrega una entrada de mapa de eventos ( ) al mapa del receptor de eventos y se agrega una función de controlador de eventos a la implementación del contenedor (. CPP).

En el ejemplo siguiente se `OnClickInCircCtrl`declara un controlador de `ClickIn` eventos, denominado , para el evento del control Circ:

[!code-cpp[NVC_MFC_AxCont#10](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_3.cpp)]

Además, la siguiente plantilla `CContainerDlg` se agrega a la implementación de la clase (. CPP) para la función miembro del controlador de eventos:

[!code-cpp[NVC_MFC_AxCont#11](../mfc/codesnippet/cpp/activex-control-containers-handling-events-from-an-activex-control_4.cpp)]

Para obtener más información sobre las macros de receptores de eventos, vea Mapas de [receptores](../mfc/reference/event-sink-maps.md) de eventos en la Referencia de biblioteca de *clases*.

#### <a name="to-create-an-event-handler-function"></a>Para crear una función de controlador de eventos

1. En la vista de clases, seleccione la clase de cuadro de diálogo que contiene el control ActiveX. Para este ejemplo, utilice `CContainerDlg`.

1. En la ventana **Propiedades** , haga clic en el botón **Eventos** .

1. En la ventana **Propiedades,** seleccione el identificador de control del control ActiveX incrustado. Para este ejemplo, utilice `IDC_CIRCCTRL1`.

   La ventana **Propiedades** muestra una lista de eventos que puede desencadenar el control ActiveX incrustado. Cualquier función miembro que se muestra en negrita ya tiene funciones de controlador asignadas.

1. Seleccione el evento que desea que controle la clase de cuadro de diálogo. Para este ejemplo, seleccione **Click**.

1. En el cuadro de lista desplegable de la derecha, seleccione ** \<Agregar> ClickCircctrl1**.

1. Haga doble clic en la nueva función de controlador desde la vista de clases para saltar al código del controlador de eventos en la implementación (. CPP) archivo `CContainerDlg`de .

## <a name="see-also"></a>Consulte también

[Contenedores de controles ActiveX](../mfc/activex-control-containers.md)
