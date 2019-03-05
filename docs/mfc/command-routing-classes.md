---
title: Clases de enrutamiento de comandos
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: 264e931ba0468cdc44f27c55e5d259948c5392b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57281974"
---
# <a name="command-routing-classes"></a>Clases de enrutamiento de comandos

Cuando el usuario interactúa con la aplicación eligiendo los menús o botones de barra de control con el mouse, la aplicación envía mensajes desde el objeto de interfaz de usuario afectado a un objeto de destino de comando adecuado. Destino del comando clases derivadas de `CCmdTarget` incluyen [CWinApp](../mfc/reference/cwinapp-class.md), [CWnd](../mfc/reference/cwnd-class.md), [CDocTemplate](../mfc/reference/cdoctemplate-class.md), [CDocument](../mfc/reference/cdocument-class.md), [CView](../mfc/reference/cview-class.md), y las clases derivadas de ellos. El marco de trabajo admite automática de comandos de enrutamiento para que los comandos pueden controlarse mediante el objeto más adecuado actualmente activo en la aplicación.

Un objeto de clase `CCmdUI` se pasa al comando de actualización de los destinos del comando la interfaz de usuario ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) controladores para que pueda actualizar el estado de la interfaz de usuario de un comando concreto (por ejemplo, para comprobar o quitar la comprobación de los elementos de menú). Llamar a funciones miembro de la `CCmdUI` objeto para actualizar el estado del objeto de interfaz de usuario. Este proceso es el mismo si el objeto de interfaz de usuario asociado con un comando determinado es un elemento de menú o un botón o ambos.

[CCmdTarget](../mfc/reference/ccmdtarget-class.md)<br/>
Actúa como clase base para todas las clases de objetos que pueden recibir y responder a los mensajes.

[CCmdUI](../mfc/reference/ccmdui-class.md)<br/>
Proporciona una interfaz de programación para actualizar los objetos de interfaz de usuario como elementos de menú o botones de barra de control. El objeto de destino del comando habilita, deshabilita, comprueba y borra el objeto de interfaz de usuario con este objeto.

## <a name="see-also"></a>Vea también

[Información general de clases](../mfc/class-library-overview.md)
