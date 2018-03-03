---
title: "Procesar mensajes de notificación en un Control Rebar | Documentos de Microsoft"
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
- RBN_ notification messages, description of
- CReBarCtrl class [MFC], notification messages sent by
- RBN_ notification messages [MFC]
- notifications [MFC], CReBarCtrl
ms.assetid: 40f43a60-0c18-4d8d-8fab-213a095624f9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22a8b584c309cd6698ddd73449fcbba866111190
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="processing-notification-messages-in-a-rebar-control"></a>Procesar mensajes de notificación en un control Rebar
En la clase primaria del control rebar, cree una `OnChildNotify` función de controlador con una instrucción switch para cualquier control rebar (`CReBarCtrl`) mensajes de notificación que desea controlar. Las notificaciones se envían a la ventana primaria cuando el usuario arrastra objetos sobre el control de rebar, cambia el diseño de las bandas rebar, elimina bandas del control rebar y así sucesivamente.  
  
 Los siguientes mensajes de notificación se pueden enviar por el objeto de control rebar:  
  
-   **RBN_AUTOSIZE se** enviados por un control rebar (creado con la **RBS_AUTOSIZE** estilo) cuando el control rebar cambia automáticamente de tamaño.  
  
-   **RBN_BEGINDRAG se** enviados por un control rebar cuando el usuario comienza a arrastrar una banda.  
  
-   **RBN_CHILDSIZE se** enviados por un control rebar cuando se cambia el tamaño de ventana secundaria de una banda.  
  
-   **RBN_DELETEDBAND** enviados por un control rebar después de que se ha eliminado una banda.  
  
-   **RBN_DELETINGBAND se** enviados por un control rebar cuando una banda se va a eliminar.  
  
-   **RBN_BEGINDRAG se** enviados por un control rebar cuando el usuario deja de arrastrar una banda.  
  
-   **RBN_GETOBJECT se** enviados por un control rebar (creado con la **RBS_REGISTERDROP** estilo) cuando se arrastra un objeto a través de una banda en el control.  
  
-   **RBN_HEIGHTCHANGE se** enviados por un control rebar cuando ha cambiado su alto.  
  
-   **RBN_LAYOUTCHANGED se** enviados por un control rebar cuando el usuario cambia el diseño de las bandas del control.  
  
 Para obtener más información sobre estas notificaciones, consulte [referencia del Control Rebar](http://msdn.microsoft.com/library/windows/desktop/bb774375) del SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

