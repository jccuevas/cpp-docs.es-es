---
title: Controlar y asignar mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 1b109a3f85ffd3311d08c3d749d543b1e625e77c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628623"
---
# <a name="message-handling-and-mapping"></a>Controlar y asignar mensajes

Esta serie de artículos describe cómo se procesan los mensajes y comandos del marco de trabajo de MFC y cómo conectarse a las funciones de controlador.

En los programas tradicionales de Windows, se tratan los mensajes de Windows en una gran instrucción switch en un procedimiento de ventana. En su lugar utiliza MFC [mapas de mensajes](../mfc/message-categories.md) para asignar mensajes a funciones miembro de clase distinto. Mapas de mensajes son más eficaces que las funciones virtuales para este propósito, y permiten mensajes controlarse en el objeto de C++ más adecuado: aplicación, documento, vista y así sucesivamente. Puede asignar un único mensaje o un intervalo de mensajes, los identificadores de comando, o identificadores de control.

WM_COMMAND (mensajes), normalmente generados por los menús, botones de barra de herramientas o aceleradores, también usar el mecanismo de mapa de mensajes. MFC define un estándar [enrutamiento](../mfc/command-routing.md) de mensajes de comando entre la aplicación, marco de ventana, vista y documentos activos en el programa. Puede invalidar esta ruta si necesita.

Mapas de mensajes también proporcionan una manera de actualizar los objetos de interfaz de usuario (por ejemplo, menús y botones de barra de herramientas), habilitar o deshabilitar para adaptarlas al contexto actual.

Para obtener información general sobre los mensajes y las colas de mensajes en Windows, consulte [mensajes y las colas de mensajes](https://msdn.microsoft.com/library/windows/desktop/ms632590) en el SDK de Windows.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

- [Cómo el marco llama a un controlador de mensajes](../mfc/how-the-framework-calls-a-handler.md)

- [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)

- [Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)

- [Asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)

- [Cómo mostrar información de comandos en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [Actualización dinámica de objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)

- [Procedimiento para crear un mapa de mensajes para una clase de plantilla](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>Vea también

[Conceptos](../mfc/mfc-concepts.md)<br/>
[Temas generales de MFC](../mfc/general-mfc-topics.md)<br/>
[CWnd (clase)](../mfc/reference/cwnd-class.md)<br/>
[CCmdTarget (clase)](../mfc/reference/ccmdtarget-class.md)
