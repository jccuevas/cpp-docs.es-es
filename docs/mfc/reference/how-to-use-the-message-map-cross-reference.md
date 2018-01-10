---
title: "Cómo: usar la referencia cruzada del mapa de mensajes | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.mfc.messages
dev_langs: C++
helpviewer_keywords: windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 25f78fb2e2c5700cbb1f7c8dcb093795ce001c13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Cómo: Usar la referencia cruzada del mapa de mensajes
En las entradas con la etiqueta \<memberFxn >, escribir su propia función miembro de una derivada [CWnd](../../mfc/reference/cwnd-class.md) clase. Utilizar cualquier nombre que desee para la función. Otras funciones, como `OnActivate`, son funciones miembro de clase `CWnd`. Si se llama, pasan el mensaje a la `DefWindowProc` la función de Windows. Para procesar mensajes de notificación de Windows, reemplace el correspondiente `CWnd` función de la clase derivada. La función debe llamar a la función reemplazada en la clase base para permitir que la clase base y Windows responden al mensaje.  
  
 En todos los casos, coloque el prototipo de función en el `CWnd`-encabezado de clase derivada y código de la entrada de mapa de mensajes, como se muestra.  
  
 Se utilizan los términos siguientes:  
  
|Término|Definición|  
|----------|----------------|  
|id|Cualquier Id. del elemento de menú definido por el usuario (**WM_COMMAND** mensajes) o el control ID (mensajes de notificación de ventana secundaria).|  
|"mensaje" y "wNotifyCode"|Id. de mensaje de Windows como se define en WINDOWS. H.|  
|nMessageVariable|Nombre de una variable que contiene el valor devuelto de la **RegisterWindowMessage** la función de Windows.|  
  
## <a name="see-also"></a>Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)

