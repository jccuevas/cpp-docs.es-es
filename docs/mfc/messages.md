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
ms.openlocfilehash: 5d7544d92d55ec4a1f6d15f3c1d4358970bf2deb
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36928346"
---
# <a name="messages"></a>Mensajes
El bucle de mensajes en el `Run` función miembro de clase `CWinApp` recupera los mensajes generados por diferentes eventos en cola. Por ejemplo, cuando el usuario hace clic en el mouse, Windows envía varios mensajes relacionados con el mouse (ratón), como WM_LBUTTONDOWN cuando se presiona el botón primario del mouse y WM_LBUTTONUP cuando se suelta el botón primario del mouse. La implementación del marco de trabajo del bucle de mensajes de la aplicación envía el mensaje a la ventana apropiada.  
  
 Las categorías de mensajes importantes se describen en [categorías de mensaje](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

