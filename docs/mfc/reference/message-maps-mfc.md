---
title: "Mapas de mensajes (MFC) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.mfc.messages"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de mensajes [C++], MFC"
  - "mensajes [C++], Windows"
  - "MFC [C++], mensajes"
  - "mensajes de Windows [C++], mapas de mensajes"
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mapas de mensajes (MFC)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En esta sección de referencia se hace una lista de todas las [macros de asignación de mensajes](../../mfc/reference/message-map-macros-mfc.md) y todas las entradas de mapa de mensajes de [CWnd](../../mfc/reference/cwnd-class.md) junto con los prototipos correspondientes de la función miembro:  
  
|Categoría|Descripción|  
|---------------|-----------------|  
|[Controlador de mensajes de WM\_COMMAND](../../mfc/reference/wm-command-message-handler.md)|Controla los mensajes de **WM\_COMMAND** generados por las selecciones de menú del usuario o las teclas de acceso del menú.|  
|[Controladores de mensajes de ventanas secundarias](../../mfc/reference/child-window-notification-message-handlers.md)|Controlan los mensajes de notificación de las ventanas secundarias.|  
|[Controladores de mensajes de WM\_](../../mfc/reference/handlers-for-wm-messages.md)|Controlan los mensajes de **WM\_**, como `WM_PAINT`.|  
|[Controladores de mensajes definidos por el usuario](../../mfc/reference/user-defined-handlers.md)|Controlan los mensajes definidos por el usuario.|  
  
 \(Para obtener una explicación de la terminología y las convenciones utilizadas en esta referencia, vea [Cómo utilizar la referencia cruzada del mapa de mensajes](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)\).  
  
 Puesto que Windows es un sistema operativo orientado a mensajes, una gran parte de la programación para el entorno Windows implica el control de mensajes.  Cada vez que tiene lugar un evento como una pulsación de tecla o un clic del mouse, se envía un mensaje a la aplicación, que debe controlar el evento.  
  
 La biblioteca MFC \(Microsoft Foundation Class\) proporciona un modelo de programación optimizado para la programación basada en mensajes.  En este modelo, los "mapas de mensajes" se utilizan para designar qué funciones controlarán los distintos mensajes para una clase determinada.  Los mapas de mensajes contienen una o varias macros que especifican qué mensajes se controlan mediante qué funciones.  Por ejemplo, un mapa de mensajes que contiene una macro `ON_COMMAND` podría tener la siguiente apariencia:  
  
 [!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/CPP/message-maps-mfc_1.cpp)]  
  
 La macro `ON_COMMAND` se utiliza para controlar los mensajes de comando generados por los menús, los botones y las teclas de aceleración.  Hay [macros](../../mfc/reference/message-map-macros-mfc.md) disponibles para asignar lo siguiente:  
  
## Mensajes de Windows  
  
-   Notificaciones del control  
  
-   Mensajes definidos por el usuario  
  
## Mensajes de comando  
  
-   Mensajes definidos por el usuario registrados  
  
-   Mensajes de actualización de la interfaz de usuario  
  
## Intervalos de mensajes  
  
-   Comandos  
  
-   Mensajes del controlador de actualización  
  
-   Notificaciones del control  
  
 Aunque las macros de mapa de mensajes son importantes, en general no es necesario utilizarlas directamente.  Esto se debe a que la ventana Propiedades crea automáticamente las entradas del mapa de mensajes en los archivos de código fuente cuando se utiliza para asociar los mensajes con las funciones de control de mensajes.  Siempre que desee editar o agregar una entrada de mapa de mensajes, puede utilizar la ventana Propiedades.  
  
> [!NOTE]
>  La ventana Propiedades no admite intervalos de mapa de mensajes.  Debe escribir estas entradas de mapa de mensajes manualmente.  
  
 Sin embargo, los mapas de mensajes son una parte importante de la biblioteca MFC \(Microsoft Foundation Class\).  Debe entender lo que hacen y consultar la documentación que se proporciona sobre ellos.  
  
## Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)