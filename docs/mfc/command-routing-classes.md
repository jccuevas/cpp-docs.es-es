---
title: Clases de enrutamiento de comandos
ms.date: 11/04/2016
f1_keywords:
- vc.classes.command
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], classes
ms.assetid: 4b50e689-2c54-4e6c-90f0-37333e22b2a1
ms.openlocfilehash: d7ff275d373cf50ab8ebe52ed454bd25cd473e11
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624823"
---
# <a name="command-routing-classes"></a>Clases de enrutamiento de comandos

A medida que el usuario interactúa con la aplicación eligiendo menús o botones de barra de control con el mouse, la aplicación envía mensajes desde el objeto de interfaz de usuario afectado a un objeto de destino de comando adecuado. Las clases de destino de comando derivadas de `CCmdTarget` incluyen [CWinApp](reference/cwinapp-class.md), [CWnd](reference/cwnd-class.md), [CDocTemplate](reference/cdoctemplate-class.md), [CDocument](reference/cdocument-class.md), [CView](reference/cview-class.md)y las clases derivadas de ellas. El marco de trabajo admite el enrutamiento automático de comandos para que los comandos se puedan controlar por el objeto más adecuado actualmente en la aplicación.

Un objeto de clase `CCmdUI` se pasa a los controladores de la interfaz de usuario de comandos de actualización ([ON_UPDATE_COMMAND_UI](reference/message-map-macros-mfc.md#on_update_command_ui)) para que pueda actualizar el estado de la interfaz de usuario para un comando determinado (por ejemplo, para comprobar o quitar la comprobación de los elementos de menú). Se llama a las funciones miembro del `CCmdUI` objeto para actualizar el estado del objeto de interfaz de usuario. Este proceso es el mismo si el objeto de interfaz de usuario asociado a un comando determinado es un elemento de menú o un botón, o ambos.

[CCmdTarget](reference/ccmdtarget-class.md)<br/>
Actúa como clase base para todas las clases de objetos que pueden recibir y responder a los mensajes.

[CCmdUI](reference/ccmdui-class.md)<br/>
Proporciona una interfaz de programación para actualizar objetos de la interfaz de usuario, como elementos de menú o botones de barra de control. El objeto de destino del comando habilita, deshabilita, comprueba y/o borra el objeto de interfaz de usuario con este objeto.

## <a name="see-also"></a>Consulte también

[Información general de clases](class-library-overview.md)
