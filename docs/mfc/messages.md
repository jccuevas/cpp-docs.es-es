---
title: Mensajes | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- messages, MFC
- messages [MFC]
ms.assetid: b1476310-a135-42ca-817c-444fb3675491
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d03eed129fd5a2a7c73f7c7948cb766813f63c34
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="messages"></a>Mensajes
El bucle de mensajes en el **ejecutar** función miembro de clase `CWinApp` recupera los mensajes generados por diferentes eventos en cola. Por ejemplo, cuando el usuario hace clic en el mouse, Windows envía varios mensajes relacionados con el mouse (ratón), como `WM_LBUTTONDOWN` cuando se presiona el botón primario del mouse y `WM_LBUTTONUP` cuando se suelta el botón primario del mouse. La implementación del marco de trabajo del bucle de mensajes de la aplicación envía el mensaje a la ventana apropiada.  
  
 Las categorías de mensajes importantes se describen en [categorías de mensaje](../mfc/message-categories.md).  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

