---
title: Controladores de mensajes | Documentos de Microsoft
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
- message handlers [MFC]
- command handling [MFC], message handlers
- handlers [MFC]
- message handling [MFC], message handler functions
- handlers [MFC], command
- handlers [MFC], message
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d1b906a49d7da7ed8505252a1759d7ea00fcda1f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="message-handlers"></a>Controladores de mensajes
En MFC, dedicada *controlador* función procesa cada mensaje independiente. Controlador de mensajes son funciones miembro de una clase. Esta documentación, utilizan los términos *función de miembro de controlador de mensajes*, *función de controlador de mensajes*, *controlador de mensajes*, y *controlador*indistintamente. Algunos tipos de controladores de mensajes también se denominan "controladores de comandos".  
  
 Escribir controladores de mensajes supone una gran parte de su trabajo en una aplicación de marco de trabajo. Esta serie de artículos describe cómo funciona el mecanismo de procesamiento de mensajes.  
  
 Lo que hace el controlador para un mensaje todo lo que desees listo en respuesta a ese mensaje. Puede crear los controladores mediante la ventana Propiedades de la clase y, a continuación, rellene el código del controlador mediante el editor de código fuente.  
  
 Puede usar todas las funciones de Microsoft Visual C++ y MFC para escribir los controladores. Para obtener una lista de todas las clases, consulte [Class Library Overview](../mfc/class-library-overview.md) en el *referencia de MFC*.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

