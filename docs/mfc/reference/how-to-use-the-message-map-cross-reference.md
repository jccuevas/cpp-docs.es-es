---
title: 'Cómo: usar la referencia cruzada del mapa de mensajes | Documentos de Microsoft'
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
ms.openlocfilehash: d59d0bfc75f654cd9f8f15ff851ad42a619e271f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33370101"
---
# <a name="how-to-use-the-message-map-cross-reference"></a>Cómo: Usar la referencia cruzada del mapa de mensajes
En las entradas con la etiqueta \<memberFxn >, escribir su propia función miembro de una derivada [CWnd](../../mfc/reference/cwnd-class.md) clase. Utilizar cualquier nombre que desee para la función. Otras funciones, como `OnActivate`, son funciones miembro de clase `CWnd`. Si se llama, pasan el mensaje a la `DefWindowProc` la función de Windows. Para procesar mensajes de notificación de Windows, reemplace el correspondiente `CWnd` función de la clase derivada. La función debe llamar a la función reemplazada en la clase base para permitir que la clase base y Windows responden al mensaje.  
  
 En todos los casos, coloque el prototipo de función en el `CWnd`-encabezado de clase derivada y código de la entrada de mapa de mensajes, como se muestra.  
  
 Se utilizan los términos siguientes:  
  
|Término|de esquema JSON|  
|----------|----------------|  
|id|Cualquier Id. del elemento de menú definido por el usuario (**WM_COMMAND** mensajes) o el control ID (mensajes de notificación de ventana secundaria).|  
|"mensaje" y "wNotifyCode"|Id. de mensaje de Windows como se define en WINDOWS. H.|  
|nMessageVariable|Nombre de una variable que contiene el valor devuelto de la **RegisterWindowMessage** la función de Windows.|  
  
## <a name="see-also"></a>Vea también  
 [Mapas de mensajes](../../mfc/reference/message-maps-mfc.md)

