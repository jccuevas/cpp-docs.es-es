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
ms.openlocfilehash: 4da2fce68c1b6fd3827bc8b5d2a40dea5e5f117c
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626174"
---
# <a name="message-sending-and-receiving"></a>Enviar y recibir mensajes

Considere la parte de envío del proceso y cómo responde el marco de trabajo.

La mayoría de los mensajes son el resultado de la interacción del usuario con el programa. Los comandos se generan mediante clics del mouse en elementos de menú o botones de la barra de herramientas o mediante pulsaciones de teclas de aceleración. El usuario también genera mensajes de Windows por, por ejemplo, al mover o cambiar el tamaño de una ventana. Se envían otros mensajes de Windows cuando se producen eventos como el inicio o la finalización de un programa, ya que Windows obtiene o pierde el foco, etc. Los mensajes de notificación de control se generan mediante clics del mouse u otras interacciones del usuario con un control, como un botón o un control de cuadro de lista en un cuadro de diálogo.

La `Run` función miembro de la clase `CWinApp` recupera los mensajes y los envía a la ventana correspondiente. La mayoría de los mensajes de comando se envían a la ventana de marco principal de la aplicación. La `WindowProc` clase predefinida por la biblioteca de clases obtiene los mensajes y los enruta de manera diferente, en función de la categoría del mensaje recibido.

Ahora considere la parte de recepción del proceso.

El receptor inicial de un mensaje debe ser un objeto de ventana. Los mensajes de Windows normalmente se controlan directamente por ese objeto Window. Los mensajes de comandos, que suelen originarse en la ventana de marco principal de la aplicación, se enrutan a la cadena de destino de comando que se describe en [enrutamiento de comandos](command-routing.md).

Cada objeto capaz de recibir mensajes o comandos tiene su propio mapa de mensajes que empareja un mensaje o comando con el nombre de su controlador.

Cuando un objeto de destino de comando recibe un mensaje o un comando, busca una coincidencia en el mapa de mensajes. Si encuentra un controlador para el mensaje, llama al controlador. Para obtener más información sobre cómo se buscan los mapas de mensajes, vea [Cómo busca el marco los mapas de mensajes](how-the-framework-searches-message-maps.md). Vuelva a consultar los [comandos de la figura en el marco de trabajo](user-interface-objects-and-command-ids.md).

## <a name="see-also"></a>Consulte también

[Cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md)
