---
title: Destinos de comando
ms.date: 11/04/2016
helpviewer_keywords:
- command targets
- command mapping
- messages, command [MFC]
- command routing [MFC], command targets
ms.assetid: b0f784e5-c6dc-4391-9e71-aa7b7dcbe9f0
ms.openlocfilehash: 59ba197174e95e42cd237c875f39f07801cb3dbe
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619314"
---
# <a name="command-targets"></a>Destinos de comando

Los [comandos de la figura en el marco de trabajo](user-interface-objects-and-command-ids.md) muestran la conexión entre un objeto de interfaz de usuario, como un elemento de menú, y la función de controlador a la que llama el marco de trabajo para llevar a cabo el comando resultante al hacer clic en el objeto.

Windows envía mensajes que no son mensajes de comandos directamente a una ventana cuyo controlador se llama para el mensaje. Sin embargo, el marco de trabajo enruta los comandos a varios objetos candidatos, denominados "destinos del comando", uno de los cuales normalmente invoca un controlador para el comando. Las funciones de controlador funcionan de la misma manera para los comandos y los mensajes estándar de Windows, pero los mecanismos por los que se llaman son diferentes, como se explica en [cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md).

## <a name="see-also"></a>Consulte también

[Mensajes y comandos en el marco](messages-and-commands-in-the-framework.md)
