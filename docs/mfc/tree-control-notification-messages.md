---
title: "Mensajes de notificación de Control de árbol | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- notifications [MFC], tree controls
- messages [MFC], notification
- CTreeCtrl class [MFC], notifications
- notifications [MFC], CTreeCtrl
- tree controls [MFC], notification messages
ms.assetid: ac7013b4-91dd-4668-bd75-439ca0680ef9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e5044416ca38f6b3ead743c571ea7175022d51fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="tree-control-notification-messages"></a>Mensajes de notificación de controles de árbol
Un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía los siguientes mensajes de notificación como **WM_NOTIFY** mensajes:  
  
|Mensaje de notificación|Descripción|  
|--------------------------|-----------------|  
|**TVN_BEGINDRAG**|Indica el inicio de una operación de arrastrar y colocar|  
|**TVN_BEGINLABELEDIT**|Indica el comienzo de la edición en contexto de etiquetas.|  
|**TVN_BEGINRDRAG**|Indica el inicio de una operación de arrastrar y colocar, con el botón secundario del mouse|  
|**TVN_DELETEITEM**|Indica la eliminación de un elemento específico|  
|**TVN_ENDLABELEDIT**|Marca el final de la edición de etiquetas|  
|**TVN_GETDISPINFO**|Solicita información que requiere el control de árbol para mostrar un elemento|  
|**TVN_ITEMEXPANDED**|Indica que la lista de un elemento primario de los elementos secundarios se ha expandido o contraído|  
|**TVN_ITEMEXPANDING**|Indica que la lista de un elemento primario de los elementos secundarios se va a expandir o contraer|  
|**TVN_KEYDOWN**|Indica un evento de teclado|  
|**TVN_SELCHANGED**|Indica que ha cambiado la selección de un elemento a otro|  
|**TVN_SELCHANGING**|Indica que la selección se va a cambiar de un elemento a otro|  
|**TVN_SETDISPINFO**|Notificación para actualizar la información mantenida para un elemento|  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

