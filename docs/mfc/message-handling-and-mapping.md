---
title: Controlar y asignar mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 0321d98d8b92af0b80259bc49e84e69b987577a4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508244"
---
# <a name="message-handling-and-mapping"></a>Controlar y asignar mensajes

En esta familia de artículos se describe cómo se procesan los mensajes y comandos en el marco de trabajo de MFC y cómo se conectan a sus funciones de controlador.

En los programas tradicionales para Windows, los mensajes de Windows se controlan en una instrucción switch grande en un procedimiento de ventana. En su lugar, MFC usa [mapas de mensajes](../mfc/message-categories.md) para asignar mensajes directos a funciones miembro de clase distintas. Los mapas de mensajes son más eficaces que las funciones virtuales para este fin y permiten que los mensajes se controlen por C++ el objeto más adecuado (aplicación, documento, vista, etc.). Puede asignar un solo mensaje o un intervalo de mensajes, ID. de comando o ID. de control.

Los mensajes WM_COMMAND (normalmente generados por menús, botones de barra de herramientas o aceleradores) también usan el mecanismo de mapa de mensajes. MFC define un [enrutamiento](../mfc/command-routing.md) estándar de mensajes de comandos entre la aplicación, la ventana de marco, la vista y los documentos activos en el programa. Puede invalidar este enrutamiento si es necesario.

Los mapas de mensajes también proporcionan una manera de actualizar objetos de la interfaz de usuario (como menús y botones de barra de herramientas), habilitando o deshabilitando para adaptarse al contexto actual.

Para obtener información general sobre mensajes y colas de mensajes en Windows, consulte [mensajes y colas](/windows/win32/winmsg/messages-and-message-queues) de mensajes en el Windows SDK.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

- [Cómo el marco de trabajo llama a un controlador de mensajes](../mfc/how-the-framework-calls-a-handler.md)

- [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)

- [Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)

- [Asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)

- [Cómo Mostrar información de comandos en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Actualización dinámica de objetos de la interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)

- [Cómo: Crear un mapa de mensajes para una clase de plantilla](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CWnd (clase)](../mfc/reference/cwnd-class.md)<br/>
[CCmdTarget (clase)](../mfc/reference/ccmdtarget-class.md)
