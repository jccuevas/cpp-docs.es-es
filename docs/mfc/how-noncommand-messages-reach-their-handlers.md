---
title: Cómo llegan a los controladores los mensajes que no son de comandos
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
ms.openlocfilehash: c7b2bf819c5305da4039fae172578298d3b4e609
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618509"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Cómo llegan a los controladores los mensajes que no son de comandos

A diferencia de los comandos, los mensajes estándar de Windows no se enrutan a través de una cadena de destinos de comando, pero suelen controlarse mediante la ventana en la que Windows envía el mensaje. La ventana puede ser una ventana de marco principal, una ventana secundaria MDI, un control estándar, un cuadro de diálogo, una vista o algún otro tipo de ventana secundaria.

En tiempo de ejecución, cada ventana de Windows se adjunta a un objeto de ventana (derivado directa o indirectamente de `CWnd` ) que tiene sus propias funciones de asignación y controlador de mensajes asociadas. El marco de trabajo usa el mapa de mensajes, como para un comando, para asignar los mensajes entrantes a los controladores.

## <a name="see-also"></a>Consulte también

[Cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md)
