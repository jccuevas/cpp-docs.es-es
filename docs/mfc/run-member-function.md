---
title: Ejecutar la función miembro | Documentos de Microsoft
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
ms.openlocfilehash: be1d7d90b4c13a23e2e3456e7371abbae61be4e9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="run-member-function"></a>Run Member (Función)
Una aplicación de marco de trabajo emplea la mayor parte de su tiempo en el [ejecutar](../mfc/reference/cwinapp-class.md#run) función miembro de clase [CWinApp](../mfc/reference/cwinapp-class.md). Tras la inicialización, `WinMain` llamadas **ejecutar** para procesar el bucle de mensajes.  
  
 **Ejecutar** recorrer un bucle de mensajes, la comprobación de la cola de mensajes para mensajes disponibles. Si hay un mensaje disponible, **ejecutar** envía para la acción. Si no hay mensajes disponibles, que a menudo es true, **ejecutar** llamadas `OnIdle` para realizar cualquier procesamiento de tiempo de inactividad que usted o el marco de trabajo puede necesitar realizada. Si no hay ningún mensaje y ningún procesamiento en inactividad para realizar, la aplicación espera hasta que ocurra algo. Cuando finaliza la aplicación, **ejecutar** llamadas `ExitInstance`. En la ilustración en [función miembro OnIdle](../mfc/onidle-member-function.md) muestra la secuencia de acciones en el bucle de mensajes.  
  
 Envío de mensajes depende del tipo de mensaje. Para obtener más información, consulte [mensajes y comandos en el marco de trabajo](../mfc/messages-and-commands-in-the-framework.md).  
  
## <a name="see-also"></a>Vea también  
 [CWinApp: la clase Application](../mfc/cwinapp-the-application-class.md)
