---
title: "Cómo llegan a mensajes sus controladores | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- messages [MFC], routing
- noncommand messages
- Windows messages [MFC], routing
- message handling [MFC], noncommand messages
ms.assetid: e7df8aef-9fae-41f4-9c11-881d8465f602
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0e6a6f30597ddb5ea68b3a5a00c35e27024fb9b0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="how-noncommand-messages-reach-their-handlers"></a>Cómo llegan a los controladores los mensajes que no son de comandos
A diferencia de los comandos, mensajes estándar de Windows no se enrutan a través de una cadena de destinos de comandos, pero normalmente se controlan mediante la ventana a la que Windows envía el mensaje. La ventana puede ser una ventana de marco principal, una ventana secundaria MDI, un control estándar, un cuadro de diálogo, una vista o algún otro tipo de ventana secundaria.  
  
 En tiempo de ejecución, cada ventana de Windows está asociada a un objeto de ventana (derivado directa o indirectamente de `CWnd`) que tiene sus propias funciones de mapa y controlador de mensaje asociado. El marco de trabajo utiliza el mapa de mensajes, como para un comando, para asignar los mensajes entrantes a los controladores.  
  
## <a name="see-also"></a>Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)

