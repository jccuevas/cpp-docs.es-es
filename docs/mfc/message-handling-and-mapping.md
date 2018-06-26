---
title: Control y asignación de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 906d84d70b3bf2ae2a9da14ce9e5b06ed92d3730
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931039"
---
# <a name="message-handling-and-mapping"></a>Controlar y asignar mensajes
Esta serie de artículos describe cómo se procesan los mensajes y comandos mediante el marco de trabajo MFC y cómo se conecta a sus funciones de controlador.  
  
 En los programas tradicionales de Windows, los mensajes de Windows se controlan en una instrucción switch de gran tamaño en un procedimiento de ventana. En su lugar utiliza MFC [mapas de mensajes](../mfc/message-categories.md) para asignar mensajes a funciones miembro de clase distintos. Mapas de mensajes son más eficaces que las funciones virtuales para este propósito, y permiten mensajes ser controladas por el objeto de C++ más adecuado: aplicación, documento, vista y así sucesivamente. Solo se puede asignar un único mensaje o un intervalo de mensajes, identificadores de comando, o identificadores de controles.  
  
 WM_COMMAND (mensajes), se genera normalmente por los menús, botones de barra de herramientas o aceleradores: usar el mecanismo de mapa de mensajes. MFC define un estándar [enrutamiento](../mfc/command-routing.md) de mensajes de comando entre la aplicación, marco de ventana, vista y documentos activos en el programa. Puede invalidar esta ruta si es necesitan.  
  
 Mapas de mensajes también proporcionan una manera para actualizar los objetos de interfaz de usuario (por ejemplo, los menús y botones de barra de herramientas), habilitar o deshabilitar para satisfacer el contexto actual.  
  
 Para obtener información general sobre los mensajes y las colas de mensajes en Windows, consulte [mensajes y las colas de mensajes](http://msdn.microsoft.com/library/windows/desktop/ms632590) en el SDK de Windows.  
  
## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea obtener más información acerca de  
  
-   [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)  
  
-   [Cómo el marco de trabajo llama a un controlador de mensajes](../mfc/how-the-framework-calls-a-handler.md)  
  
-   [Cómo busca el marco los mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md)  
  
-   [Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)  
  
-   [Asignación de mensajes a funciones](../mfc/reference/mapping-messages-to-functions.md)  
  
-   [Cómo mostrar información sobre los comandos en la barra de estado](../mfc/how-to-display-command-information-in-the-status-bar.md)  
  
-   [Actualización dinámica de objetos de interfaz de usuario](../mfc/how-to-update-user-interface-objects.md)  
  
-   [Procedimiento para crear un mapa de mensajes para una clase de plantilla](../mfc/how-to-create-a-message-map-for-a-template-class.md)  
  
## <a name="see-also"></a>Vea también  
 [Conceptos](../mfc/mfc-concepts.md)   
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [CWnd (clase)](../mfc/reference/cwnd-class.md)   
 [CCmdTarget (clase)](../mfc/reference/ccmdtarget-class.md)
