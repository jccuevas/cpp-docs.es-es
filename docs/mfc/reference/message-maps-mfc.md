---
title: Mapas (MFC) de mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.messages
dev_langs: C++
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 958f308a089f2f503159b2ce56c2096595fc7613
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="message-maps-mfc"></a>Mapas de mensajes (MFC)
Esta sección de la referencia enumeran todos los [macros de asignación de mensajes](../../mfc/reference/message-map-macros-mfc.md) y todos los [CWnd](../../mfc/reference/cwnd-class.md) prototipos de función de las entradas de mapa de mensajes junto con el miembro correspondiente:  
  
|Categoría|Descripción|  
|--------------|-----------------|  
|ON\_controlador de mensajes de comando|Controla `WM_COMMAND` mensajes generados por las selecciones de menú del usuario o las teclas de acceso de menús.|  
|[Controladores de mensajes de notificación de ventana secundaria](../../mfc/reference/child-window-notification-message-handlers.md)|Controlan los mensajes de notificación de las ventanas secundarias.|  
|[Controladores de mensajes WM_](../../mfc/reference/handlers-for-wm-messages.md)|Controlar `WM_` mensajes, como `WM_PAINT`.|  
|[Controladores de mensajes definidos por el usuario](../../mfc/reference/user-defined-handlers.md)|Controlan los mensajes definidos por el usuario.|  
  
 (Para obtener una explicación de la terminología y las convenciones utilizadas en esta referencia, vea [cómo utilizar la referencia cruzada del mapa de mensajes](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)  
  
 Puesto que Windows es un sistema operativo orientado a mensajes, una gran parte de la programación para el entorno Windows implica el control de mensajes. Cada vez que tiene lugar un evento como una pulsación de tecla o un clic del mouse, se envía un mensaje a la aplicación, que debe controlar el evento.  
  
 La biblioteca MFC (Microsoft Foundation Class) proporciona un modelo de programación optimizado para la programación basada en mensajes. En este modelo, los "mapas de mensajes" se utilizan para designar qué funciones controlarán los distintos mensajes para una clase determinada. Los mapas de mensajes contienen una o varias macros que especifican qué mensajes se controlan mediante qué funciones. Por ejemplo, un mapa de mensajes que contiene una macro `ON_COMMAND` podría tener la siguiente apariencia:  
  
 [!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]  
  
 La macro `ON_COMMAND` se utiliza para controlar los mensajes de comando generados por los menús, los botones y las teclas de aceleración. [Macros](../../mfc/reference/message-map-macros-mfc.md) están disponibles para asignar lo siguiente:  
  
## <a name="windows-messages"></a>Mensajes de Windows  
  
-   Notificaciones del control  
  
-   Mensajes definidos por el usuario  
  
## <a name="command-messages"></a>Mensajes de comando  
  
-   Mensajes definidos por el usuario registrados  
  
-   Mensajes de actualización de la interfaz de usuario  
  
## <a name="ranges-of-messages"></a>Intervalos de mensajes  
  
-   Comandos  
  
-   Mensajes del controlador de actualización  
  
-   Notificaciones del control  
  
 Aunque las macros de mapa de mensajes son importantes, en general no es necesario utilizarlas directamente. Esto se debe a que la ventana Propiedades crea automáticamente las entradas del mapa de mensajes en los archivos de código fuente cuando se utiliza para asociar los mensajes con las funciones de control de mensajes. Siempre que desee editar o agregar una entrada de mapa de mensajes, puede utilizar la ventana Propiedades.  
  
> [!NOTE]
>  La ventana Propiedades no admite intervalos de mapa de mensajes. Debe escribir estas entradas de mapa de mensajes manualmente.  
  
 Sin embargo, los mapas de mensajes son una parte importante de la biblioteca MFC (Microsoft Foundation Class). Debe entender lo que hacen y consultar la documentación que se proporciona sobre ellos.  
  
## <a name="see-also"></a>Vea también  
 [Estructuras, estilos, devoluciones de llamada y mapas de mensajes](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)

