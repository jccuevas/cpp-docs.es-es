---
title: Asignación de mensajes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7324da5eaff15d240cabbaede2c2982021361257
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46410986"
---
# <a name="mapping-messages"></a>Asignar mensajes

Cada clase de marco de trabajo que puede recibir mensajes o comandos tiene su propio "mapa de mensajes". El marco de trabajo usa mapas de mensajes que se conectarán mensajes y comandos para las funciones de controlador. Cualquier clase derivada de la clase `CCmdTarget` puede tener un mapa de mensajes. Otros artículos explican los mapas de mensajes en detalle y describen cómo usarlos.

A pesar del nombre "mapa de mensajes," mapas de mensajes tratan ambos mensajes y comandos, las tres categorías de mensajes que aparecen en [categorías de mensaje](../mfc/message-categories.md).

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

