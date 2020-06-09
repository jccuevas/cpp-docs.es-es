---
title: error de Hadoop
ms.date: 11/04/2016
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
ms.openlocfilehash: f36dab679a2e41910b2445a7dab36f5786081563
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84624280"
---
# <a name="messages"></a>error de Hadoop

El bucle de mensajes de la `Run` función miembro de clase `CWinApp` recupera los mensajes en cola generados por varios eventos. Por ejemplo, cuando el usuario hace clic con el mouse, Windows envía varios mensajes relacionados con el mouse, como WM_LBUTTONDOWN cuando se presiona el botón primario del mouse y WM_LBUTTONUP cuando se suelta el botón primario del mouse. La implementación del marco del bucle de mensajes de aplicación envía el mensaje a la ventana correspondiente.

Las categorías de mensajes importantes se describen en [categorías de mensajes](message-categories.md).

## <a name="see-also"></a>Consulte también

[Mensajes y comandos en el marco](messages-and-commands-in-the-framework.md)
