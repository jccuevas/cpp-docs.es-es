---
title: Mensaje de mapas (MFC) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- message maps [C++], MFC
- Windows messages [C++], message maps
- messages [C++], Windows
- MFC [C++], messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5187996fc377bca8633360082d07f7ec8a68ee57
ms.openlocfilehash: bb31d35e221c9f5d06dc34408bed500b4a18b077
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="message-maps-mfc"></a>Mapas de mensajes (MFC)
Esta sección de la referencia enumeran todos los [macros de asignación de mensajes](../../mfc/reference/message-map-macros-mfc.md) y todos los [CWnd](../../mfc/reference/cwnd-class.md) prototipos de función de las entradas de mapa de mensajes junto con el miembro correspondiente:  
  
|Categoría|Descripción|  
|--------------|-----------------|  
|[Controlador de mensajes WM_COMMAND](../../mfc/reference/wm-command-message-handler.md)|Controla **WM_COMMAND** mensajes generados por las selecciones de menú de usuario o las teclas de acceso de menú.|  
|[Controladores de mensajes de notificación de ventana secundaria](../../mfc/reference/child-window-notification-message-handlers.md)|Controlan los mensajes de notificación de las ventanas secundarias.|  
|[Controladores de mensajes WM_](../../mfc/reference/handlers-for-wm-messages.md)|Controlar **WM_** mensajes, como `WM_PAINT`.|  
|[Controladores de mensajes definidos por el usuario](../../mfc/reference/user-defined-handlers.md)|Controlan los mensajes definidos por el usuario.|  
  
 (Para obtener una explicación de la terminología y las convenciones utilizadas en esta referencia, consulte [cómo utilizar la referencia cruzada del mapa de mensajes](../../mfc/reference/how-to-use-the-message-map-cross-reference.md).)  
  
 Puesto que Windows es un sistema operativo orientado a mensajes, una gran parte de la programación para el entorno Windows implica el control de mensajes. Cada vez que tiene lugar un evento como una pulsación de tecla o un clic del mouse, se envía un mensaje a la aplicación, que debe controlar el evento.  
  
 La biblioteca MFC (Microsoft Foundation Class) proporciona un modelo de programación optimizado para la programación basada en mensajes. En este modelo, los "mapas de mensajes" se utilizan para designar qué funciones controlarán los distintos mensajes para una clase determinada. Los mapas de mensajes contienen una o varias macros que especifican qué mensajes se controlan mediante qué funciones. Por ejemplo, un mapa de mensajes que contiene una macro `ON_COMMAND` podría tener la siguiente apariencia:  
  
 [!code-cpp[NVC_MFCMessageMaps Nº&16;](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]  
  
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


