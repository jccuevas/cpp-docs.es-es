---
title: Cómo llegan a los controladores los mensajes que no son de comandos
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: 4b9fb0a72b330380f0207db9968199a7e4c3d9b3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57295063"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Cómo llegan a los controladores los mensajes que no son de comandos

A diferencia de los comandos, los mensajes de Windows estándar no se enrutan a través de una cadena de destinos de comandos, pero normalmente se controlan mediante la ventana a la que Windows envía el mensaje. La ventana puede ser una ventana de marco principal, una ventana secundaria MDI, un control estándar, un cuadro de diálogo, una vista o algún otro tipo de ventana secundaria.

En tiempo de ejecución, cada ventana de Windows está asociada a un objeto de ventana (deriva directa o indirectamente `CWnd`) que tiene sus propias funciones de asignación y el controlador de mensaje asociado. El marco de trabajo usa el mapa de mensajes, en cuanto a un comando, para asignar los mensajes entrantes a los controladores.

## <a name="see-also"></a>Vea también

[Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)
