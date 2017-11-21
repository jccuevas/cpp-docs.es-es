---
title: Destinos de comando | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 16a2599b97d88cf4e36b15a70203fc0ca91ca2a2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="command-targets"></a>Destinos de comando
En la ilustración [comandos en el marco de trabajo](../mfc/user-interface-objects-and-command-ids.md) muestra la conexión entre un objeto de interfaz de usuario, como un elemento de menú y la función de controlador que llama el marco de trabajo para llevar a cabo el comando resultante cuando se hace clic en el objeto.  
  
 Windows envía los mensajes que no son mensajes de comandos directamente en una ventana cuyo controlador para el mensaje, a continuación, se llama. Sin embargo, el marco de trabajo enruta los comandos a un número de objetos candidatos, denominados "destinos de comando": uno de los cuales, normalmente, invoca un controlador para el comando. Las funciones de controlador funcionan del mismo modo para comandos y mensajes de Windows estándares, pero los mecanismos por el que se denominan son diferentes, como se explica en [cómo el marco de trabajo llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

