---
title: OnCmdMsg (Controlador)
ms.date: 11/04/2016
f1_keywords:
- OnCmdMsg
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
ms.openlocfilehash: 5114fe53a5bac345eb6a55fb6c371f7bc1f698ef
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624025"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg (Controlador)

Para realizar el enrutamiento de comandos, cada destino de comando llama a la `OnCmdMsg` función miembro del siguiente destino del comando en la secuencia. Los destinos de comando usan `OnCmdMsg` para determinar si pueden controlar un comando y enrutarlo a otro destino de comando si no pueden controlarlo.

Cada clase de destino de comando puede invalidar la `OnCmdMsg` función miembro. Las invalidaciones permiten que cada clase dirija comandos a un destino siguiente determinado. Por ejemplo, una ventana de marco siempre enruta los comandos a su vista o ventana secundaria actual, tal como se muestra en la [ruta de comando](command-routing.md)de tabla estándar.

La `CCmdTarget` implementación predeterminada de `OnCmdMsg` usa el mapa de mensajes de la clase de destino de comando para buscar una función de controlador para cada mensaje de comando que recibe, de la misma manera que se busca en los mensajes estándar. Si encuentra una coincidencia, llama al controlador. La búsqueda de mapas de mensajes se explica en [Cómo busca el marco los mapas de mensajes](how-the-framework-searches-message-maps.md).

## <a name="see-also"></a>Consulte también

[Cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md)
