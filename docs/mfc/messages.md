---
title: Mensajes | Documentos de Microsoft
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
ms.openlocfilehash: abd49410f9982788e9403f0cb83ca8656473417d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="messages"></a>Mensajes
El bucle de mensajes en el **ejecutar** función miembro de clase `CWinApp` recupera los mensajes generados por diferentes eventos en cola. Por ejemplo, cuando el usuario hace clic en el mouse, Windows envía varios mensajes relacionados con el mouse (ratón), como `WM_LBUTTONDOWN` cuando se presiona el botón primario del mouse y `WM_LBUTTONUP` cuando se suelta el botón primario del mouse. La implementación del marco de trabajo del bucle de mensajes de la aplicación envía el mensaje a la ventana apropiada.  
  
 Las categorías de mensajes importantes se describen en [categorías de mensaje](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

