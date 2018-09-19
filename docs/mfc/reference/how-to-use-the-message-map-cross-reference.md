---
title: 'Cómo: utilizar la referencia cruzada del mapa de mensajes | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.mfc.messages
dev_langs:
- C++
helpviewer_keywords:
- windows [MFC], message maps
ms.assetid: 2e863d23-9e58-45ba-b5e4-a8ceefccd0c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf76d8f7bb86bf3325a072df80a45e2f0a3ad985
ms.sourcegitcommit: 6408139d5f5ff8928f056bde93d20eecb3520361
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/02/2018
ms.locfileid: "37338903"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Cómo: Usar la referencia cruzada del mapa de mensajes
En las entradas con la etiqueta \<memberFxn >, escribir su propia función de miembro para un derivado [CWnd](../../mfc/reference/cwnd-class.md) clase. Asigne a la función de cualquier nombre que desee. Las demás funciones, como `OnActivate`, son funciones miembro de clase `CWnd`. Si se llama, pasan el mensaje a la `DefWindowProc` función de Windows. Para procesar mensajes de notificación de Windows, reemplace el correspondiente `CWnd` función en la clase derivada. La función debe llamar a la función invalidada en su clase base para permitir que la clase base y Windows responden al mensaje.  
  
 En todos los casos, coloque el prototipo de función en el `CWnd`: encabezado de la clase derivada y la entrada de asignación de mensaje, como se muestra de código.  
  
 Se utilizan los términos siguientes:  
  
|Término|de esquema JSON|  
|----------|----------------|  
|id|Cualquier Id. de elemento de menú definido por el usuario (mensajes WM_COMMAND) o el Id. de control (mensajes de notificación de ventana secundaria).|  
|"mensaje" y "wNotifyCode"|Identificadores de mensajes de Windows tal como se define en WINDOWS. H.|  
|nMessageVariable|Nombre de una variable que contiene el valor devuelto por la `RegisterWindowMessage` función de Windows.|  
  
## <a name="see-also"></a>Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)

