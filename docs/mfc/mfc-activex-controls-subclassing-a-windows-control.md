---
title: 'Controles ActiveX MFC: Crear subclases de un Control de Windows | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- precreatewindow
- IsSubclassed
dev_langs: C++
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
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 3e41eefdf1c1be2d0e91061e0efce5f5408c1848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-subclassing-a-windows-control"></a>Controles ActiveX MFC: Creación de subclases de un control de Windows
En este artículo se describe el proceso de creación de subclases de un control común de Windows para crear un control ActiveX. Creación de subclases de un Windows existente control es un método rápido para desarrollar un control ActiveX. El nuevo control tendrán las capacidades del control de Windows con subclases, tales como dibujar y responder a clics del mouse. Ejemplo de controles de ActiveX de MFC [botón](../visual-cpp-samples.md) es un ejemplo de creación de subclases de un control de Windows.  
  
 Para crear subclases de un control de Windows, complete las tareas siguientes:  
  
-   [Reemplazar las funciones miembro IsSubclassedControl y PreCreateWindow de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [Modifique la función miembro OnDraw](#_core_modifying_the_ondraw_member_function)  
  
-   [Controlar los mensajes de control de ActiveX (OCM) reflejados hacia el control](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  Gran parte de este trabajo se realiza automáticamente por el Asistente para controles ActiveX si selecciona el control que puede crear subclases utilizando la **seleccionar clase de ventana primaria** la lista desplegable en el **configuración del Control** página.  
  
 Vea el artículo de Knowledge Base Q243454 para obtener más información sobre la creación de subclases de un control.  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a>Reemplazar IsSubclassedControl y PreCreateWindow  
 Para invalidar `PreCreateWindow` y `IsSubclassedControl`, agregue las siguientes líneas de código para el `protected` sección de la declaración de clase de control:  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 En el archivo de implementación (. (CPP), agregue las siguientes líneas de código para implementar las dos funciones reemplazadas:  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 Observe que, en este ejemplo, el control button de Windows se especifica en `PreCreateWindow`. Sin embargo, se pueden crear subclases de los controles estándar de Windows. Para obtener más información sobre controles estándar de Windows, vea [controles](../mfc/controls-mfc.md).  
  
 Cuando la creación de subclases de un control de Windows, puede que desee especificar el estilo de ventana concreta (**WS_**) o el estilo de ventana extendido (**WS_EX_**) marcas que se usará en la creación de la ventana del control. Puede establecer valores para estos parámetros en el `PreCreateWindow` función miembro modificando la **cs.style** y **cs.dwExStyle** campos de la estructura. Las modificaciones realizadas en estos campos se deben realizar con un `OR` operación para conservar los indicadores predeterminados establecidos por la clase `COleControl`. Por ejemplo, si el control está creando subclases del control de botón y desea que el control aparezca como una casilla de verificación, inserte la siguiente línea de código en la implementación de `CSampleCtrl::PreCreateWindow`, antes de la instrucción return:  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 Esta operación agrega la **BS_CHECKBOX** estilo marca, dejando el indicador de estilo predeterminado (**WS_CHILD**) de la clase `COleControl` intacta.  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a>Modificar la función miembro OnDraw  
 Si desea que el control con subclases para mantener la misma apariencia que el control de Windows correspondiente, el `OnDraw` función de miembro para el control debe contener sólo una llamada a la `DoSuperclassPaint` función de miembro, como en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 El `DoSuperclassPaint` función miembro, implementada por `COleControl`, usa el procedimiento de ventana del control de Windows para dibujar el control en el contexto de dispositivo especificado, dentro del rectángulo delimitador. Esto hace que el control sea visible incluso cuando no esté activo.  
  
> [!NOTE]
>  El `DoSuperclassPaint` función miembro solo funcionarán con los tipos de control que permiten a un contexto de dispositivo que se pasará como el **wParam** de un `WM_PAINT` mensaje. Esto incluye algunos de los controles de Windows estándares, como **barra de desplazamiento** y **botón**y todos los controles comunes. Para los controles que no admiten este comportamiento, tendrá que proporcionar su propio código para mostrar correctamente un control inactivo.  
  
##  <a name="_core_handling_reflected_window_messages"></a>Controlar los mensajes de ventana reflejados  
 Controles de Windows normalmente envían determinados mensajes de ventana a su ventana primaria. Algunos de estos mensajes, como **WM_COMMAND**, proporcionar una notificación de una acción por el usuario. Otros, como `WM_CTLCOLOR`, se utilizan para obtener información de la ventana primaria. Un control ActiveX normalmente se comunica con la ventana primaria por otros medios. Las notificaciones se comunican mediante eventos activadores (enviando notificaciones de eventos) y obtener información sobre el contenedor del control se obtiene mediante el acceso a propiedades de ambiente del contenedor. Dado que estas técnicas de comunicación existen, contenedores de controles ActiveX no se esperan para procesar los mensajes de ventana enviados por el control.  
  
 Para evitar el contenedor reciba los mensajes de ventana enviados por un control de Windows crearon subclases, `COleControl` crea una ventana adicional para actuar como elemento primario del control. Esta ventana adicional, denominada "reflector", se crea solo para un control ActiveX que las subclases de una ventana de controlan y tiene el mismo tamaño y la posición que la ventana de control. La ventana de reflector intercepta determinados mensajes de ventana y envía de nuevo al control. El control, en el procedimiento de ventana, a continuación, puede procesar estos mensajes reflejados realizando acciones apropiadas para un control ActiveX (por ejemplo, desencadenar un evento). Vea [identificadores de mensajes de ventana reflejados](../mfc/reflected-window-message-ids.md) para obtener una lista de windows interceptados mensajes y sus correspondientes mensajes reflejan.  
  
 Un contenedor de controles ActiveX puede estar diseñado para realizar la reflexión de mensajes, lo que elimina la necesidad de `COleControl` para crear la ventana de reflector y reducir el tiempo de ejecución sobrecarga para un control de Windows con subclases. `COleControl`detecta si el contenedor admite esta capacidad mediante la comprobación de una propiedad de ambiente MessageReflect con un valor de **TRUE**.  
  
 Para controlar un mensaje de ventana reflejado, agregue una entrada para el mapa de mensajes de control e implementar una función de controlador. Dado que mensajes reflejados no forman parte del conjunto estándar de mensajes definidos por Windows, vista de clases no admite la adición de estos controladores de mensajes. Sin embargo, no es difícil agregar un controlador manualmente.  
  
 Para agregar un controlador de mensajes para un mensaje de ventana reflejada manualmente haga lo siguiente:  
  
-   En la clase de control. Archivo H, declare una función de controlador. La función debe tener un tipo de valor devuelto de **LRESULT** y dos parámetros, con tipos de **WPARAM** y **LPARAM**, respectivamente. Por ejemplo:  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   En la clase de control. CPP, agregue un `ON_MESSAGE` entrada al mapa de mensajes. Los parámetros de esta entrada deben ser el identificador del mensaje y el nombre de la función de controlador. Por ejemplo:  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/cpp/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   También en el. Archivo CPP, implemente la **OnOcmCommand** función de miembro para procesar el mensaje reflejado. El **wParam** y **lParam** parámetros son los mismos que los del mensaje de ventana original.  
  
 De un ejemplo de cómo refleja se procesan los mensajes, consulte el ejemplo de controles ActiveX en MFC [botón](../visual-cpp-samples.md). Muestra un **OnOcmCommand** controlador que detecta el **BN_CLICKED** código de notificación y responde activando (envío) de un evento de clic.  
  
## <a name="see-also"></a>Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)

