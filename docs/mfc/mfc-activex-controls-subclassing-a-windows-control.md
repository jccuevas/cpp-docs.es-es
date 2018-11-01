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
ms.openlocfilehash: 24284af7766f0fd968ca08724440509bc171fba6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50576649"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Controles ActiveX MFC: Creación de subclases de un control de Windows

En este artículo se describe el proceso de creación de subclases de un control común de Windows para crear un control ActiveX. Creación de subclases de una existente Windows control es una forma rápida de desarrollar un control ActiveX. El nuevo control tendrán las capacidades del control de Windows con subclases, tales como dibujar y responder a clics del mouse. Ejemplo de los controles ActiveX de MFC [botón](../visual-cpp-samples.md) es un ejemplo de creación de subclases de un control de Windows.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no se recomienda para nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que sustituyen a ActiveX, vea [controles ActiveX](activex-controls.md).

Para crear una subclase de un control de Windows, complete las tareas siguientes:

- [Invalidar las funciones de miembro IsSubclassedControl y PreCreateWindow de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modifique la función miembro OnDraw](#_core_modifying_the_ondraw_member_function)

- [Controlar los mensajes de control de ActiveX (OCM) reflejados en el control](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Gran parte de este trabajo se realiza automáticamente por el Asistente para controles ActiveX si selecciona el control que se puede crear subclases utilizando la **seleccionar clase de ventana primaria** lista desplegable en el **configuración del Control** página.

##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Reemplazar IsSubclassedControl y PreCreateWindow

Para invalidar `PreCreateWindow` y `IsSubclassedControl`, agregue las siguientes líneas de código para el **protegido** sección de la declaración de clase de control:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

En el archivo de implementación (. (CPP), agregue las siguientes líneas de código para implementar las dos funciones reemplazadas:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Tenga en cuenta que, en este ejemplo, el Windows control de botón se especifica en `PreCreateWindow`. Sin embargo, se pueden crear subclases de los controles de Windows estándares. Para obtener más información sobre los controles de Windows estándar, consulte [controles](../mfc/controls-mfc.md).

Cuando la creación de subclases de un control de Windows, puede especificar el estilo de ventana concreta (WS_) o las marcas de estilo (WS_EX_) extendido de ventana que se usará en la creación de la ventana del control. Puede establecer valores para estos parámetros en el `PreCreateWindow` función miembro modificando el `cs.style` y el `cs.dwExStyle` estructurar los campos. Las modificaciones en estos campos se deben realizar con un **o** operación, se han de conservar las marcas predeterminadas que se establecen mediante la clase `COleControl`. Por ejemplo, si el control es crear subclases del control de botón y desea que el control aparezca como una casilla de verificación, inserte la siguiente línea de código en la implementación de `CSampleCtrl::PreCreateWindow`, antes de la instrucción return:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Esta operación agrega el estilo BS_CHECKBOX, dejando el indicador de estilo predeterminado (WS_CHILD) de la clase `COleControl` intactos.

##  <a name="_core_modifying_the_ondraw_member_function"></a> Modificación de la función miembro OnDraw

Si desea que el control con subclases para mantener la misma apariencia que el control de Windows correspondiente, el `OnDraw` función miembro para el control debe contener sólo una llamada a la `DoSuperclassPaint` la función miembro, como se muestra en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

El `DoSuperclassPaint` función miembro, implementado por `COleControl`, el procedimiento de ventana del control de Windows se utiliza para dibujar el control en el contexto de dispositivo especificado, dentro del rectángulo delimitador. Esto hace que el control sea visible incluso cuando no esté activo.

> [!NOTE]
>  El `DoSuperclassPaint` miembro funcione solo con esos tipos de control que permiten a un contexto de dispositivo que se pasarán como el *wParam* de un mensaje WM_PAINT. Esto incluye algunos de los controles de Windows estándares, como la barra de desplazamiento y un botón y todos los controles comunes. Para los controles que no admiten este comportamiento, deberá proporcionar su propio código para mostrar correctamente un control inactivo.

##  <a name="_core_handling_reflected_window_messages"></a> Controlar los mensajes de ventana reflejados

Controles de Windows normalmente envían determinados mensajes de ventana a su ventana primaria. Algunos de estos mensajes, tales como WM_COMMAND, proporcionan una notificación de una acción por parte del usuario. Otros, como WM_CTLCOLOR, se usan para obtener información de la ventana primaria. Un control ActiveX normalmente se comunica con la ventana primaria por otros medios. Las notificaciones se comunican mediante la activación de eventos (envío de notificaciones de eventos) y se obtiene información sobre el contenedor de control mediante el acceso a las propiedades de ambiente del contenedor. Ya que estas técnicas de comunicación, los contenedores de controles ActiveX no se esperan para procesar los mensajes de ventana enviados por el control.

Para evitar que reciba los mensajes de ventana enviados por un control con subclases de Windows, el contenedor `COleControl` crea una ventana adicional para que actúe como elemento primario del control. Esta ventana adicional, denominada "reflector", se crea solo para un control ActiveX que las subclases de un Windows controlan y tiene el mismo tamaño y posición como la ventana de control. La ventana de reflector intercepta determinados mensajes de ventana y los envía al control. El control, en su procedimiento de ventana, a continuación, puede procesar estos mensajes reflejados realizando acciones apropiadas para un control ActiveX (por ejemplo, desencadenar un evento). Consulte [reflejan identificadores de mensaje de ventana](../mfc/reflected-window-message-ids.md) para obtener una lista de ventanas interceptados mensajes y sus correspondientes mensajes reflejan.

Un contenedor de controles ActiveX puede estar diseñado para realizar la reflexión de mensajes, eliminando la necesidad de `COleControl` para crear la ventana de reflector y reducir el tiempo de ejecución sobrecarga de un control con subclases de Windows. `COleControl` detecta si el contenedor admite esta funcionalidad mediante la comprobación de una propiedad de ambiente MessageReflect con un valor de **TRUE**.

Para controlar un mensaje de ventana reflejada, agregar una entrada en el mapa de mensajes de control e implementar una función de controlador. Porque los mensajes reflejados no forman parte del conjunto estándar de mensajes definidos por Windows, vista de clases no admite la adición de estos controladores de mensajes. Sin embargo, no es difícil agregar manualmente un controlador.

Para agregar un controlador de mensajes para un mensaje de ventana reflejada manualmente lo siguiente:

- En la clase del control. Archivo de H, declare una función de controlador. La función debe tener un tipo de valor devuelto de **LRESULT** y dos parámetros con tipos **WPARAM** y **LPARAM**, respectivamente. Por ejemplo:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- En la clase del control. CPP, agregue una entrada ON_MESSAGE al mapa de mensajes. Los parámetros de esta entrada deben ser el identificador de mensaje y el nombre de la función de controlador. Por ejemplo:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- También en el. Archivo CPP, implemente el `OnOcmCommand` función de miembro para procesar el mensaje reflejado. El *wParam* y *lParam* parámetros son los mismos que los del mensaje de ventana original.

Para un ejemplo de cómo se refleja los mensajes se procesan, consulte el ejemplo de controles ActiveX MFC [botón](../visual-cpp-samples.md). Muestra una `OnOcmCommand` controlador que detecta el código de notificación BN_CLICKED y responde mediante la activación (enviar) un `Click` eventos.

## <a name="see-also"></a>Vea también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

