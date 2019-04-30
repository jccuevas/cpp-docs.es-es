---
title: Destinos de comando
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: ed3d6a68967dc7f4244f887ae34760fdb99fa7f5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388519"
---
# <a name="command-targets"></a>Destinos de comando

La figura [comandos en el marco](../mfc/user-interface-objects-and-command-ids.md) muestra la conexión entre un objeto de interfaz de usuario, como un elemento de menú y la función de controlador que llama el marco de trabajo para llevar a cabo el comando resultante cuando se hace clic en el objeto.

Windows envía los mensajes que no son mensajes de comandos directamente en una ventana cuyo controlador para el mensaje, a continuación, se llama. Sin embargo, el marco de trabajo enruta los comandos a un número de objetos de candidato, denominados "destinos de comando", uno de los cuales normalmente invoca un controlador para el comando. Las funciones de controlador funcionan del mismo modo para comandos y mensajes de Windows estándar, pero los mecanismos por el que se les llama son diferentes, como se explica en [cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)
