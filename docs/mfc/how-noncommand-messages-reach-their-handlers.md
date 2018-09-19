---
title: Cómo llegan a mensajes sus controladores | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3999c74bf7a612acb998e7a044c12948d7679d9b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343887"
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Cómo llegan a los controladores los mensajes que no son de comandos
A diferencia de los comandos, mensajes estándar de Windows no se enrutan a través de una cadena de destinos de comandos, pero normalmente se controlan mediante la ventana a la que Windows envía el mensaje. La ventana puede ser una ventana de marco principal, una ventana secundaria MDI, un control estándar, un cuadro de diálogo, una vista o algún otro tipo de ventana secundaria.  
  
 En tiempo de ejecución, cada ventana de Windows está asociada a un objeto de ventana (derivado directa o indirectamente de `CWnd`) que tiene sus propias funciones de mapa y controlador de mensaje asociado. El marco de trabajo utiliza el mapa de mensajes, como para un comando, para asignar los mensajes entrantes a los controladores.  
  
## <a name="see-also"></a>Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)

