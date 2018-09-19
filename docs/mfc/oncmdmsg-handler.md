---
title: OnCmdMsg (controlador) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- OnCmdMsg
dev_langs:
- C++
helpviewer_keywords:
- messages, routing
- handlers [MFC]
- command routing [MFC], OnCmdMsg handler
- handlers, OnCmdMessage [MFC]
- OnCmdMessage method [MFC]
ms.assetid: 8df07024-506f-47e7-bba9-1c3bc5ad8ab6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0657b05619a966ed171630d00adcd9303af7e18b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347034"
---
# <a name="oncmdmsg-handler"></a>OnCmdMsg (Controlador)
Para llevar a cabo el enrutamiento de comandos, llama a cada destino del comando el `OnCmdMsg` función miembro del destino del comando siguiente en la secuencia. Uso de destinos de comandos `OnCmdMsg` para determinar si puede controlar un comando y las enrute a otro destino de comando si no se puede controlarla.  
  
 Cada clase de destino del comando puede reemplazar la `OnCmdMsg` función miembro. Las invalidaciones permiten cada clase enrutar comandos hacia un siguiente destino concreto. Una ventana de marco, por ejemplo, siempre enruta los comandos hacia su ventana secundaria actual o una vista, como se muestra en la tabla [enrutamiento de comandos estándar](../mfc/command-routing.md).  
  
 El valor predeterminado `CCmdTarget` implementación de `OnCmdMsg` utiliza la asignación de mensaje de la clase de destino del comando para buscar una función controladora para cada mensaje de comando que recibe, de la misma manera que se buscan los mensajes estándares. Si encuentra a una coincidencia, llama al controlador. Búsqueda de mapa de mensajes se explica en [cómo el marco de trabajo búsquedas de mapas de mensajes](../mfc/how-the-framework-searches-message-maps.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)

