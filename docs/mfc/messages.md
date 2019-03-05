---
title: Mensajes
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: 8e1bfd1baa8ffef76ba31912fc619c4217696683
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57300081"
---
# <a name="messages"></a>Mensajes

El bucle de mensajes en el `Run` función miembro de clase `CWinApp` recupera en cola los mensajes generados por varios eventos. Por ejemplo, cuando el usuario hace clic con el mouse, Windows envía varios mensajes relacionados con el mouse, como WM_LBUTTONDOWN cuando se presiona el botón primario del mouse y WM_LBUTTONUP cuando se suelta el botón primario del mouse. La implementación de .NET framework de bucle de mensajes de aplicación envía el mensaje a la ventana correspondiente.

Se describen las principales categorías de mensajes en [categorías de mensaje](../mfc/message-categories.md).

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)
