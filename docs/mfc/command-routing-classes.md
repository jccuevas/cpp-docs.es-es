---
title: Clases de enrutamiento de comandos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- vc.classes.command
dev_langs:
- C++
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f3e05046ac6754dd585bb1fbf51420ef862af7be
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="command-routing-classes"></a>Clases de enrutamiento de comandos
Cuando el usuario interactúa con la aplicación eligiendo los menús o botones de barra de control con el mouse, la aplicación envía mensajes desde el objeto de interfaz de usuario afectado a un objeto de destino del comando adecuado. Destino del comando clases derivadas de `CCmdTarget` incluyen [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), y las clases que derivan de ellos. El marco de trabajo admite el enrutamiento de comandos automática para que los comandos pueden ser controlados por el objeto más adecuado actualmente activo en la aplicación.  
  
 Un objeto de clase `CCmdUI` se pasa al comando de actualización de los destinos de comando interfaz de usuario ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) controladores para que pueda actualizar el estado de la interfaz de usuario de un comando concreto (por ejemplo, para comprobar o quitar la comprobación de elementos de menú). Llamar a funciones miembro de la `CCmdUI` objeto que se va a actualizar el estado del objeto de interfaz de usuario. Este proceso es el mismo si el objeto de interfaz de usuario asociado a un comando determinado es un elemento de menú o un botón o ambas cosas.  
  
 [CCmdTarget](../mfc/reference/ccmdtarget-class.md)  
 Actúa como clase base para todas las clases de objetos que pueden recibir y responder a mensajes.  
  
 [CCmdUI](../mfc/reference/ccmdui-class.md)  
 Proporciona una interfaz de programación para actualizar los objetos de interfaz de usuario como elementos de menú o botones de barra de control. El objeto de destino del comando habilita, deshabilita, comprueba o borra el objeto de interfaz de usuario con este objeto.  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../mfc/class-library-overview.md)

