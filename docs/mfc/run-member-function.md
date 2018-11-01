---
title: Ejecute la función miembro | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- WinMain method [MFC]
ms.assetid: 24ab7597-2354-495b-9a20-2c8ccc7385b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 446b1b6fc2a5265e2c4eb8a608ff8b4f0028c57d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46408237"
---
# <a name="run-member-function"></a>Run Member (Función)

Una aplicación de marco de trabajo pasa la mayor parte de su tiempo en el [ejecutar](../mfc/reference/cwinapp-class.md#run) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md). Tras la inicialización, `WinMain` llamadas `Run` para procesar el bucle de mensajes.

`Run` recorre un bucle de mensajes, comprobación de la cola de mensajes para mensajes disponibles. Si un mensaje está disponible, `Run` lo distribuye para la acción. Si no hay mensajes disponibles, que a menudo es true, `Run` llamadas `OnIdle` para realizar cualquier procesamiento de tiempo de inactividad que usted o el marco de trabajo que necesite realizada. Si no hay ningún mensaje y realizar ningún procesamiento en inactividad, la aplicación espera hasta que suceda algo. Cuando la aplicación termina, `Run` llamadas `ExitInstance`. La figura [función miembro OnIdle](../mfc/onidle-member-function.md) muestra la secuencia de acciones en el bucle de mensajes.

Envío del mensaje depende del tipo de mensaje. Para obtener más información, consulte [mensajes y comandos en el marco de trabajo](../mfc/messages-and-commands-in-the-framework.md).

## <a name="see-also"></a>Vea también

[CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
