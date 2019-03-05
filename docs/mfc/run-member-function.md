---
title: Run Member (Función)
ms.date: 11/04/2016
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
ms.openlocfilehash: 8271a10ad7439d2795dcc45d667b23b0932a0486
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271832"
---
# <a name="run-member-function"></a>Run Member (Función)

Una aplicación de marco de trabajo pasa la mayor parte de su tiempo en el [ejecutar](../mfc/reference/cwinapp-class.md#run) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md). Tras la inicialización, `WinMain` llamadas `Run` para procesar el bucle de mensajes.

`Run` recorre un bucle de mensajes, comprobación de la cola de mensajes para mensajes disponibles. Si un mensaje está disponible, `Run` lo distribuye para la acción. Si no hay mensajes disponibles, que a menudo es true, `Run` llamadas `OnIdle` para realizar cualquier procesamiento de tiempo de inactividad que usted o el marco de trabajo que necesite realizada. Si no hay ningún mensaje y realizar ningún procesamiento en inactividad, la aplicación espera hasta que suceda algo. Cuando la aplicación termina, `Run` llamadas `ExitInstance`. La figura [función miembro OnIdle](../mfc/onidle-member-function.md) muestra la secuencia de acciones en el bucle de mensajes.

Envío del mensaje depende del tipo de mensaje. Para obtener más información, consulte [mensajes y comandos en el marco de trabajo](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Vea también

[CWinApp: La clase de aplicación](../mfc/cwinapp-the-application-class.md)
