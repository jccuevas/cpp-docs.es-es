---
title: Asignar mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], about message maps
- mappings [MFC], commands
- commands [MFC], mapping
- command mapping [MFC]
- message handling [MFC], connecting to handler functions
- commands [MFC], connecting to handler functions
- mappings [MFC], messages
- messages [MFC], mapping
ms.assetid: 996f0652-0698-4b8c-b893-cdaa836d9d0f
ms.openlocfilehash: 16d6d7725d82bed6c9bfc02e408b68dcf7ffe5e4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625490"
---
# <a name="mapping-messages"></a>Asignar mensajes

Cada clase de Framework que puede recibir mensajes o comandos tiene su propio "mapa de mensajes". El marco de trabajo usa mapas de mensajes para conectar mensajes y comandos a sus funciones de controlador. Cualquier clase derivada de `CCmdTarget` la clase puede tener un mapa de mensajes. Otros artículos explican los mapas de mensajes en detalle y describen cómo usarlos.

A pesar del nombre "mapa de mensajes", los mapas de mensajes controlan tanto los mensajes como los comandos, las tres categorías de mensajes que aparecen en [categorías de mensajes](message-categories.md).

## <a name="see-also"></a>Consulte también

[Mensajes y comandos en el marco](messages-and-commands-in-the-framework.md)
