---
title: 'Controles ActiveX MFC: Creación de subclases de un control de Windows'
ms.date: 09/12/2018
f1_keywords:
- precreatewindow
- IsSubclassed
helpviewer_keywords:
- OnDraw method, MFC ActiveX controls
- subclassing
- DoSuperclassPaint method [MFC]
- subclassing Windows controls
- subclassing, Windows controls
- reflected messages, in ActiveX controls
- PreCreateWindow method, overriding
- MFC ActiveX controls [MFC], subclassed controls
- MFC ActiveX controls [MFC], creating
- IsSubclassed method [MFC]
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
ms.openlocfilehash: c68a7c9764e7f52131a90d38db22d2645eed9a4f
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625414"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Controles ActiveX MFC: Creación de subclases de un control de Windows

En este artículo se describe el proceso de creación de subclases de un control de Windows común para crear un control ActiveX. La creación de subclases de un control de Windows existente es una forma rápida de desarrollar un control ActiveX. El nuevo control tendrá las capacidades del control de Windows de subclase, como pintar y responder a los clics del mouse. El [botón](../overview/visual-cpp-samples.md) de ejemplo controles ActiveX de MFC es un ejemplo de subclase de un control de Windows.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe usarse para el nuevo desarrollo. Para obtener más información sobre las tecnologías modernas que reemplazan a ActiveX, vea [controles ActiveX](activex-controls.md).

Para subclases de un control de Windows, complete las siguientes tareas:

- [Reemplazar las funciones miembro IsSubclassedControl y PreCreateWindow de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modificar la función miembro OnDraw](#_core_modifying_the_ondraw_member_function)

- [Controlar los mensajes de control ActiveX (OCM) reflejados en el control](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Gran parte de este trabajo lo lleva a cabo el Asistente para controles ActiveX si selecciona control para el que se van a crear subclases mediante la lista desplegable **seleccionar clase de ventana primaria** de la página **configuración del control** .

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Reemplazar IsSubclassedControl y PreCreateWindow

Para reemplazar `PreCreateWindow` y `IsSubclassedControl` , agregue las siguientes líneas de código a la sección **protegida** de la declaración de clase del control:

[!code-cpp[NVC_MFC_AxSub#1](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

En el archivo de implementación del control (. CPP), agregue las siguientes líneas de código para implementar las dos funciones invalidadas:

[!code-cpp[NVC_MFC_AxSub#2](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Observe que, en este ejemplo, el control de botón de Windows se especifica en `PreCreateWindow` . Sin embargo, se pueden crear subclases de todos los controles estándar de Windows. Para obtener más información sobre los controles estándar de Windows, consulte [controles](controls-mfc.md).

Al crear subclases de un control de Windows, es posible que desee especificar las marcas de estilo de ventana (WS_) o de estilo de ventana extendida (WS_EX_) que se van a utilizar en la creación de la ventana del control. Puede establecer los valores de estos parámetros en la `PreCreateWindow` función miembro modificando los `cs.style` campos de la `cs.dwExStyle` estructura y. Las modificaciones en estos campos deben realizarse mediante una operación **o** , para conservar las marcas predeterminadas que se establecen mediante la clase `COleControl` . Por ejemplo, si el control está subclase del control de botón y desea que el control aparezca como una casilla, inserte la siguiente línea de código en la implementación de `CSampleCtrl::PreCreateWindow` , antes de la instrucción return:

[!code-cpp[NVC_MFC_AxSub#3](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Esta operación agrega la marca de estilo BS_CHECKBOX, a la vez que deja intacta la marca de estilo predeterminada (WS_CHILD) de la clase `COleControl` .

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Modificar la función miembro OnDraw

Si desea que el control subclase tenga la misma apariencia que el control de Windows correspondiente, la `OnDraw` función miembro del control solo debe contener una llamada a la `DoSuperclassPaint` función miembro, como en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxSub#4](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

La `DoSuperclassPaint` función miembro, implementada por `COleControl` , usa el procedimiento de ventana del control de Windows para dibujar el control en el contexto de dispositivo especificado, dentro del rectángulo delimitador. Esto hace que el control sea visible incluso cuando no está activo.

> [!NOTE]
> La `DoSuperclassPaint` función miembro solo funcionará con los tipos de control que permitan pasar un contexto de dispositivo como *wParam* de un mensaje de WM_PAINT. Esto incluye algunos de los controles estándar de Windows, como SCROLLBAR y BUTTON, y todos los controles comunes. En el caso de los controles que no admiten este comportamiento, tendrá que proporcionar su propio código para mostrar correctamente un control inactivo.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Control de mensajes de ventana reflejados

Los controles de Windows normalmente envían ciertos mensajes de ventana a su ventana primaria. Algunos de estos mensajes, como WM_COMMAND, proporcionan una notificación de una acción por parte del usuario. Otros, como WM_CTLCOLOR, se usan para obtener información de la ventana primaria. Normalmente, un control ActiveX se comunica con la ventana primaria por otros medios. Las notificaciones se comunican mediante eventos de activación (envío de notificaciones de eventos) y la información sobre el contenedor de control se obtiene mediante el acceso a las propiedades de ambiente del contenedor. Dado que estas técnicas de comunicación existen, no se espera que los contenedores de controles ActiveX procesen los mensajes de ventana enviados por el control.

Para evitar que el contenedor reciba los mensajes de ventana enviados por un control de Windows de subclase, `COleControl` crea una ventana adicional para que sirva como elemento primario del control. Esta ventana adicional, denominada "reflector", solo se crea para un control ActiveX que cree subclases de un control de Windows y tenga el mismo tamaño y posición que la ventana de control. La ventana de reflector intercepta determinados mensajes de ventana y los devuelve al control. El control, en el procedimiento de ventana, puede procesar estos mensajes reflejados realizando acciones adecuadas para un control ActiveX (por ejemplo, desencadenando un evento). Vea [identificadores de mensaje de ventana reflejada](reflected-window-message-ids.md) para obtener una lista de mensajes de Windows interceptados y sus mensajes reflejados correspondientes.

Un contenedor de controles ActiveX puede diseñarse para realizar la reflexión del mensaje en sí, lo que elimina la necesidad de `COleControl` crear la ventana de reflector y reducir la sobrecarga en tiempo de ejecución de un control de Windows de subclase. `COleControl`detecta si el contenedor admite esta capacidad comprobando si hay una propiedad de ambiente MessageReflect con un valor de **true**.

Para controlar un mensaje de ventana reflejado, agregue una entrada al mapa de mensajes de control e implemente una función de controlador. Dado que los mensajes reflejados no forman parte del conjunto estándar de mensajes definidos por Windows, Vista de clases no admite la adición de controladores de mensajes. Sin embargo, no es difícil agregar un controlador manualmente.

Para agregar manualmente un controlador de mensajes para un mensaje de ventana reflejado, haga lo siguiente:

- En la clase control. H, declare una función de controlador. La función debe tener un tipo de valor devuelto de **LRESULT** y dos parámetros, con los tipos **wParam** e **lParam**, respectivamente. Por ejemplo:

   [!code-cpp[NVC_MFC_AxSub#5](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- En la clase control. Archivo CPP, agregue una entrada ON_MESSAGE al mapa de mensajes. Los parámetros de esta entrada deben ser el identificador de mensaje y el nombre de la función de controlador. Por ejemplo:

   [!code-cpp[NVC_MFC_AxSub#7](codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- También en. Archivo CPP, implemente la `OnOcmCommand` función miembro para procesar el mensaje reflejado. Los parámetros *wParam* e *lParam* son los mismos que los del mensaje de ventana original.

Para obtener un ejemplo de cómo se procesan los mensajes reflejados, consulte el [botón](../overview/visual-cpp-samples.md)de ejemplo controles ActiveX MFC. Muestra un `OnOcmCommand` controlador que detecta el código de notificación de BN_CLICKED y responde desencadenando (enviando) un `Click` evento.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](mfc-activex-controls.md)
