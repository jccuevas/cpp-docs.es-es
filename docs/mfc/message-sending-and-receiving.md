---
title: Enviar y recibir mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- Windows messages [MFC], handling in MFC
- control-notification messages [MFC]
- messages [MFC], receiving
- messages [MFC], MFC
- MFC, messages
- messages [MFC], sending
ms.assetid: 9ce189cb-b259-4c3b-b6f2-9cfbed18b98b
ms.openlocfilehash: bda261f4141a7ceb4e678535d9012650818fabce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384054"
---
# <a name="message-sending-and-receiving"></a>Enviar y recibir mensajes

Tenga en cuenta la parte del proceso y cómo responde el marco de envío.

Más mensajes el resultado de la interacción del usuario con el programa. Los comandos se generan mediante clics del mouse en los elementos de menú o botones de barra de herramientas o presionar teclas de aceleración. El usuario también genera mensajes de Windows, por ejemplo, mover o cambiar el tamaño de una ventana. Otros mensajes de Windows se envían cuando se produzcan eventos, como el inicio del programa o la terminación, como windows obtengan o pierden el foco y así sucesivamente. Se generan mensajes de notificación de control por clics del mouse u otras interacciones de usuario con un control, como un control de botón o un cuadro de lista en un cuadro de diálogo.

El `Run` función miembro de clase `CWinApp` recupera los mensajes y los envía a la ventana correspondiente. La mayoría de los mensajes de comando se envían a la ventana de marco principal de la aplicación. El `WindowProc` predefinidos por el obtiene de la biblioteca de clases de los mensajes y enruta de forma diferente, según la categoría del mensaje recibido.

Ahora considere la posibilidad de la parte del proceso de recepción.

El receptor de un mensaje inicial debe ser un objeto de ventana. Los mensajes de Windows normalmente se administran directamente mediante ese objeto de ventana. Mensajes de comando, normalmente que se originan en la ventana de marco principal de la aplicación, se enrutan a la cadena de destino del comando que se describe en [enrutamiento de comandos](../mfc/command-routing.md).

Cada objeto capaz de recibir mensajes o comandos tiene su propio mensaje de mapa que empareja un mensaje o un comando con el nombre de su controlador.

Cuando un objeto de destino del comando recibe un mensaje o un comando, busca su mapa de mensajes para una coincidencia. Si encuentra un controlador para el mensaje, llama al controlador. Para obtener más información acerca de cómo se buscan los mapas de mensajes, vea [cómo el marco de las búsquedas de mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md). Consulte de nuevo en la ilustración [comandos en el marco](../mfc/user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Vea también

[Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)
