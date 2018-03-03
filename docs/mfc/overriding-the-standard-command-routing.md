---
title: "Invalidar el enrutamiento de comandos estándar | Documentos de Microsoft"
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
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6a8f926a2aa9ed48dac24f75850876bbd1e04ef4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="overriding-the-standard-command-routing"></a>Invalidar el enrutamiento de comandos estándar
En raras ocasiones cuando se debe implementar alguna variación del enrutamiento de marco estándar, se puede invalidar. La idea consiste en cambiar el enrutamiento en una o más clases invalidando `OnCmdMsg` en esas clases. Hacer esto:  
  
-   En la clase que rompe el orden para pasar a un objeto no predeterminado.  
  
-   En el nuevo objeto no predeterminado o en destinos de comando a su vez podría pasar comandos a.  
  
 Si inserta un nuevo objeto en el enrutamiento, su clase debe ser una clase de destino del comando. En las versiones reemplaza de `OnCmdMsg`, asegúrese de llamar a la versión que está reemplazando. Consulte la [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg) función miembro de clase `CCmdTarget` en el *referencia de MFC* y las versiones de clases como `CView` y **CDocument** en el código de origen proporcionado para obtener ejemplos.  
  
## <a name="see-also"></a>Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)

