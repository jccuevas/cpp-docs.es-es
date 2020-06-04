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
ms.openlocfilehash: ccebbad22be92b84fa2fd84434f788484d332cce
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375997"
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Controles ActiveX MFC: Creación de subclases de un control de Windows

En este artículo se describe el proceso para subclases de un control común de Windows para crear un control ActiveX. La subclase de un control de Windows existente es una forma rápida de desarrollar un control ActiveX. El nuevo control tendrá las capacidades del control de Windows subclase, como pintar y responder a los clics del ratón. El ejemplo de controles ActiveX de MFC [BUTTON](../overview/visual-cpp-samples.md) es un ejemplo de subclase de un control de Windows.

>[!IMPORTANT]
> ActiveX es una tecnología heredada que no debe utilizarse para el nuevo desarrollo. Para obtener más información acerca de las tecnologías modernas que reemplazan a ActiveX, vea [Controles ActiveX](activex-controls.md).

Para subclase un control de Windows, realice las siguientes tareas:

- [Invalidar el IsSubclassedControl y PreCreateWindow funciones miembro de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)

- [Modificar la función miembro OnDraw](#_core_modifying_the_ondraw_member_function)

- [Controlar los mensajes de control ActiveX (OCM) reflejados en el control](#_core_handling_reflected_window_messages)

   > [!NOTE]
   > Gran parte de este trabajo se realiza por el Asistente para controles ActiveX si selecciona el control que se va a subclase mediante la lista desplegable Seleccionar clase de **ventana principal** en la página **Configuración** de control.

## <a name="overriding-issubclassedcontrol-and-precreatewindow"></a><a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Reemplazar IsSubclassedControl y PreCreateWindow

Para `PreCreateWindow` invalidar `IsSubclassedControl`y , agregue las siguientes líneas de código a la sección **protegida** de la declaración de clase de control:

[!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]

En el archivo de implementación del control (. CPP), agregue las siguientes líneas de código para implementar las dos funciones invalidadas:

[!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]

Observe que, en este ejemplo, el control `PreCreateWindow`de botón de Windows se especifica en . Sin embargo, los controles estándar de Windows se pueden subclases. Para obtener más información sobre los controles estándar de Windows, vea [Controles](../mfc/controls-mfc.md).

Al crear subclases de un control de Windows, es posible que desee especificar determinados indicadores de estilo de ventana (WS_) o de estilo de ventana extendida (WS_EX_) que se usarán en la creación de la ventana del control. Puede establecer valores para estos `PreCreateWindow` parámetros en `cs.style` la `cs.dwExStyle` función miembro modificando los campos y la estructura. Las modificaciones de estos campos se deben realizar mediante una operación `COleControl` **OR,** para conservar las marcas predeterminadas establecidas por la clase . Por ejemplo, si el control está subclasificando el control BUTTON y desea que el control aparezca `CSampleCtrl::PreCreateWindow`como una casilla de verificación, inserte la siguiente línea de código en la implementación de , antes de la instrucción return:

[!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]

Esta operación agrega el indicador de estilo BS_CHECKBOX, dejando `COleControl` intacta la marca de estilo predeterminada (WS_CHILD) de la clase.

## <a name="modifying-the-ondraw-member-function"></a><a name="_core_modifying_the_ondraw_member_function"></a>Modificación de la función miembro OnDraw

Si desea que el control subclase mantenga la misma apariencia `OnDraw` que el control de Windows correspondiente, la función miembro del control debe contener solo una llamada a la `DoSuperclassPaint` función miembro, como en el ejemplo siguiente:

[!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]

La `DoSuperclassPaint` función miembro, `COleControl`implementada por , usa el procedimiento de ventana del control de Windows para dibujar el control en el contexto de dispositivo especificado, dentro del rectángulo delimitador. Esto hace que el control sea visible incluso cuando no está activo.

> [!NOTE]
> La `DoSuperclassPaint` función miembro solo funcionará con los tipos de control que permiten pasar un contexto de dispositivo como *wParam* de un mensaje de WM_PAINT. Esto incluye algunos de los controles estándar de Windows, como SCROLLBAR y BUTTON, y todos los controles comunes. Para los controles que no admiten este comportamiento, tendrá que proporcionar su propio código para mostrar correctamente un control inactivo.

## <a name="handling-reflected-window-messages"></a><a name="_core_handling_reflected_window_messages"></a>Manejo de mensajes de ventana reflejados

Los controles de Windows normalmente envían determinados mensajes de ventana a su ventana primaria. Algunos de estos mensajes, como WM_COMMAND, proporcionan una notificación de una acción del usuario. Otros, como WM_CTLCOLOR, se utilizan para obtener información de la ventana primaria. Un control ActiveX normalmente se comunica con la ventana primaria por otros medios. Las notificaciones se comunican mediante la activación de eventos (envío de notificaciones de eventos) y la información sobre el contenedor de control se obtiene mediante el acceso a las propiedades ambientales del contenedor. Dado que existen estas técnicas de comunicación, no se espera que los contenedores de controles ActiveX procesen los mensajes de ventana enviados por el control.

Para evitar que el contenedor reciba los mensajes de `COleControl` ventana enviados por un control de Windows subclase, crea una ventana adicional que sirve como elemento primario del control. Esta ventana adicional, denominada "reflector", se crea solo para un control ActiveX que subclase un control de Windows y tiene el mismo tamaño y posición que la ventana de control. La ventana del reflector intercepta ciertos mensajes de ventana y los envía de vuelta al control. El control, en su procedimiento de ventana, puede procesar estos mensajes reflejados realizando las acciones adecuadas para un control ActiveX (por ejemplo, desencadenar un evento). Consulte ID de mensajes de [ventana reflejados](../mfc/reflected-window-message-ids.md) para obtener una lista de los mensajes de Windows interceptados y sus mensajes reflejados correspondientes.

Un contenedor de control ActiveX puede estar diseñado para `COleControl` realizar la reflexión de mensajes, lo que elimina la necesidad de crear la ventana del reflector y reduce la sobrecarga en tiempo de ejecución de un control de Windows subclasificado. `COleControl`detecta si el contenedor admite esta capacidad comprobando si hay una propiedad ambiente MessageReflect con un valor **TRUE**.

Para controlar un mensaje de ventana reflejado, agregue una entrada al mapa de mensajes de control e implemente una función de controlador. Dado que los mensajes reflejados no forman parte del conjunto estándar de mensajes definido por Windows, la vista de clases no admite la adición de dichos controladores de mensajes. Sin embargo, no es difícil agregar un controlador manualmente.

Para agregar un controlador de mensajes para un mensaje de ventana reflejado manualmente, haga lo siguiente:

- En la clase de control . H, declare una función de controlador. La función debe tener un tipo de valor devuelto **lRESULT** y dos parámetros, con los tipos **WPARAM** y **LPARAM**, respectivamente. Por ejemplo:

   [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]

- En la clase de control . CPP, agregue una entrada ON_MESSAGE al mapa de mensajes. Los parámetros de esta entrada deben ser el identificador de mensaje y el nombre de la función de controlador. Por ejemplo:

   [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]

- También en el . CPP, implemente `OnOcmCommand` la función miembro para procesar el mensaje reflejado. Los *parámetros wParam* y *lParam* son los mismos que los del mensaje de ventana original.

Para obtener un ejemplo de cómo se procesan los mensajes reflejados, consulte el ejemplo [BUTTON](../overview/visual-cpp-samples.md)de controles ActiveX de MFC. Muestra un `OnOcmCommand` controlador que detecta el código de notificación BN_CLICKED `Click` y responde desencadenando (enviando) un evento.

## <a name="see-also"></a>Consulte también

[Controles ActiveX MFC](../mfc/mfc-activex-controls.md)
