---
title: "Controles ActiveX MFC: Creaci&#243;n de subclases de un control de Windows | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "precreatewindow"
  - "IsSubclassed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoSuperclassPaint (método)"
  - "IsSubclassed (método)"
  - "controles ActiveX en MFC, crear"
  - "controles ActiveX en MFC, controles en subclase"
  - "OnDraw (método), controles ActiveX en MFC"
  - "PreCreateWindow (método), reemplazar"
  - "mensajes reflejados, en controles ActiveX"
  - "creación de subclases"
  - "creación de subclases de controles de Windows"
  - "creación de subclases, controles de Windows"
ms.assetid: 3236d4de-401f-49b7-918d-c84559ecc426
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Controles ActiveX MFC: Creaci&#243;n de subclases de un control de Windows
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se describe el proceso para crear subclases un control común de Windows para crear un control ActiveX.  Crear subclases de un control existente de Windows es una forma rápida de desarrollar un control ActiveX.  El nuevo control tendrá las capacidades de control derivado de Windows, como dibujo y responder a los clics del mouse.  El ejemplo de controles ActiveX de MFC [BUTTON](../top/visual-cpp-samples.md) es un ejemplo de cómo crear subclases de un control de Windows.  
  
 Para crear subclases de un control de Windows, realice las tareas siguientes:  
  
-   [Reemplace las funciones miembro de IsSubclassedControl y de PreCreateWindow de COleControl](#_core_overriding_issubclassedcontrol_and_precreatewindow)  
  
-   [Modifique la función miembro de OnDraw](#_core_modifying_the_ondraw_member_function)  
  
-   [Controlar cualquier mensaje de control ActiveX \(OCM\) reflejado al control](#_core_handling_reflected_window_messages)  
  
    > [!NOTE]
    >  Gran parte de este trabajo se hace automáticamente por el asistente para controles ActiveX si selecciona el control que se va a crear subclases utilizando la lista desplegable de **Select Parent Window Class** en la página de **Configuración del control** .  
  
 Vea el artículo Q243454 de Knowledge Base para obtener más información sobre cómo crear subclases de un control.  
  
##  <a name="_core_overriding_issubclassedcontrol_and_precreatewindow"></a> Reemplazar IsSubclassedControl y PreCreateWindow  
 Para reemplazar `PreCreateWindow` y `IsSubclassedControl`, agregue las siguientes líneas de código a la sección de `protected` de la declaración de clase de control:  
  
 [!code-cpp[NVC_MFC_AxSub#1](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_1.h)]  
  
 En el archivo de implementación del control \(.CPP\), agregue las siguientes líneas de código para implementar las dos funciones invalidadas:  
  
 [!code-cpp[NVC_MFC_AxSub#2](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_2.cpp)]  
  
 Observe que, en este ejemplo, el control de botón de Windows está especificado en `PreCreateWindow`.  Sin embargo, cualquier control estándar de Windows puede crear subclases.  Para obtener más información sobre los controles estándar de Windows, vea [Controles](../mfc/controls-mfc.md).  
  
 Al crear subclases de un control de Windows, puede especificar el estilo de ventana determinada \(**WS\_**\) o el estilo de ventana extendida \(**WS\_EX\_**\) marca para utilizar en la ventana de control.  Puede establecer valores para estos parámetros en la función miembro de `PreCreateWindow` modificando **cs.style** y los campos de la estructura de **cs.dwExStyle** .  Las modificaciones a estos campos deben crear mediante una operación de `OR` , mantener los marcadores predeterminado establecidos por la clase `COleControl`.  Por ejemplo, si el control está creando subclases el control button y desea que el control aparezca como casilla, inserte la línea siguiente de código en la implementación de `CSampleCtrl::PreCreateWindow`, antes de la instrucción return:  
  
 [!code-cpp[NVC_MFC_AxSub#3](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_3.cpp)]  
  
 Esta operación agrega el indicador de estilo de **BS\_CHECKBOX** , mientras que permite el indicador de estilo predeterminado \(**WS\_CHILD**\) de la clase `COleControl` intacto.  
  
##  <a name="_core_modifying_the_ondraw_member_function"></a> Modificar la función miembro de OnDraw  
 Si desea que el control derivado conservar el mismo aspecto que el control correspondiente de Windows, la función miembro de `OnDraw` para el control debe contener sólo una llamada a la función miembro de `DoSuperclassPaint` , como en el ejemplo siguiente:  
  
 [!code-cpp[NVC_MFC_AxSub#4](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_4.cpp)]  
  
 La función miembro de `DoSuperclassPaint` , implementada por `COleControl`, utiliza el procedimiento de ventana de controles de Windows para dibujar el control en el contexto especificado del dispositivo, dentro del rectángulo delimitador.  Esto hace que el control visible aunque no esté activo.  
  
> [!NOTE]
>  La función miembro de `DoSuperclassPaint` sólo funcionará con los tipos de control que permiten que un contexto del dispositivo se pasa como **wParam** de un mensaje de `WM_PAINT` .  Esto incluye algunos de los controles estándar de Windows, como **barra de desplazamiento** y **BUTTON**, y todos los controles comunes.  Para los controles que no admiten este comportamiento, tendrá que proporcionar el propio código para mostrar correctamente un control inactivo.  
  
##  <a name="_core_handling_reflected_window_messages"></a> Administrar mensajes reflejados de la ventana  
 Los controles de Windows envían normalmente determinados mensajes de la ventana a su ventana primaria.  Algunos de estos mensajes, como **WM\_COMMAND**, proporcionan notificación de una acción del usuario.  Otros, como `WM_CTLCOLOR`, se usan para obtener información de la ventana primaria.  Un control ActiveX comunica normalmente con la ventana primaria por otros medios.  Las notificaciones se comunicadas desencadenar eventos \(que envían notificaciones de eventos\), e información sobre el contenedor de control se obtiene acceso a las propiedades de ambiente del contenedor.  Dado que existen estas técnicas de comunicación, no se espera que los contenedores de controles ActiveX procesen los mensajes de la ventana enviada por el control.  
  
 Para evitar que el contenedor reciba los mensajes de la ventana enviados por un control derivado de Windows, `COleControl` crea una ventana adicional para actuar como elemento primario del control.  Esta ventana adicional, denominada “reflector”, solo se crea para un control ActiveX que cree subclases un control de Windows y tiene el mismo tamaño y la posición como ventana de control.  Mensajes de ventana de las intersecciones de ventana reflector ciertos y los envía de nuevo al control.  El control, en el procedimiento de la ventana, puede procesar estos mensajes reflejados con acciones adecuados para un control ActiveX \(por ejemplo, desencadena un evento\).  Vea [Identificadores de mensajes reflejados de la ventana](../mfc/reflected-window-message-ids.md) para una lista de mensajes interceptados de las ventanas y sus mensajes reflejados correspondientes.  
  
 Un contenedor de controles ActiveX se puede diseñar para realizar la reflexión de mensaje propio, eliminando la necesidad de `COleControl` de crear la ventana reflector y reduce la sobrecarga del tiempo de ejecución para un control derivado de Windows.  `COleControl` detecta si el contenedor admite esta capacidad comprobar si hay una propiedad de ambiente de MessageReflect con un valor de **VERDADERO**.  
  
 Para controlar un mensaje reflejado desde la ventana, agregar una entrada al mapa de mensajes de controles e implementar una función controladora.  Dado que los mensajes reflejados no forman parte del conjunto estándar de los mensajes definidos por Windows, la vista de clases no admite agregar a estos controladores de mensajes.  Sin embargo, no es difícil agregar un controlador manualmente.  
  
 Para agregar un controlador de mensajes para un mensaje reflejado desde la ventana haga manualmente el siguiente:  
  
-   En la clase de control. El archivo de h, declara una función controladora.  La función debe tener un tipo de valor devuelto de **LRESULT** y dos parámetros, con tipos **WPARAM** y **LPARAM**, respectivamente.  Por ejemplo:  
  
     [!code-cpp[NVC_MFC_AxSub#5](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_5.h)]  
    [!code-cpp[NVC_MFC_AxSub#6](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_6.h)]  
  
-   En el archivo de clase control .CPP, agregue una entrada de `ON_MESSAGE` al mapa de mensajes.  Los parámetros de esta entrada debe ser el identificador de mensaje y el nombre de la función controladora.  Por ejemplo:  
  
     [!code-cpp[NVC_MFC_AxSub#7](../mfc/codesnippet/CPP/mfc-activex-controls-subclassing-a-windows-control_7.cpp)]  
  
-   También en el archivo de .CPP, implemente la función miembro de **OnOcmCommand** para procesar el mensaje reflejado.  Los parámetros de **wParam** y de **lParam** son iguales que los del mensaje original de la ventana.  
  
 Para obtener un ejemplo de cómo se procesan los mensajes reflejados, consulte el ejemplo de controles ActiveX de MFC [BUTTON](../top/visual-cpp-samples.md).  Muestra un controlador de **OnOcmCommand** que detecte el código de notificación de **BN\_CLICKED** y responder desencadenando \(transporte\) un evento Click.  
  
## Vea también  
 [Controles ActiveX MFC](../mfc/mfc-activex-controls.md)