---
title: Mensajes | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f25c9cc70cec598f975bbd242af83597311bdc7c
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392260"
---
# <a name="messages"></a>Mensajes

El bucle de mensajes en el `Run` función miembro de clase `CWinApp` recupera en cola los mensajes generados por varios eventos. Por ejemplo, cuando el usuario hace clic con el mouse, Windows envía varios mensajes relacionados con el mouse, como WM_LBUTTONDOWN cuando se presiona el botón primario del mouse y WM_LBUTTONUP cuando se suelta el botón primario del mouse. La implementación de .NET framework de bucle de mensajes de aplicación envía el mensaje a la ventana correspondiente.

Se describen las principales categorías de mensajes en [categorías de mensaje](../mfc/message-categories.md).

## <a name="see-also"></a>Vea también

[Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

