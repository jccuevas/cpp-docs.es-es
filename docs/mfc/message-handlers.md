---
title: Controladores de mensajes | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: be4ccf9ec33e5ddf497193c1942e9f300f8cae57
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347635"
---
# <a name="message-handlers"></a>Controladores de mensajes
En MFC, dedicada *controlador* función procesa cada mensaje independiente. Controlador de mensajes son funciones miembro de una clase. Esta documentación, utilizan los términos *función de miembro de controlador de mensajes*, *función de controlador de mensajes*, *controlador de mensajes*, y *controlador*indistintamente. Algunos tipos de controladores de mensajes también se denominan "controladores de comandos".  
  
 Escribir controladores de mensajes supone una gran parte de su trabajo en una aplicación de marco de trabajo. Esta serie de artículos describe cómo funciona el mecanismo de procesamiento de mensajes.  
  
 Lo que hace el controlador para un mensaje todo lo que desees listo en respuesta a ese mensaje. Puede crear los controladores mediante la ventana Propiedades de la clase y, a continuación, rellene el código del controlador mediante el editor de código fuente.  
  
 Puede usar todas las funciones de Microsoft Visual C++ y MFC para escribir los controladores. Para obtener una lista de todas las clases, consulte [Class Library Overview](../mfc/class-library-overview.md) en el *referencia de MFC*.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

