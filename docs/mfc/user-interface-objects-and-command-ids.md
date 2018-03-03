---
title: Objetos de interfaz de usuario e identificadores de comando | Documentos de Microsoft
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
- keyboard shortcuts, associating with IDs
- MFC, command routing
- toolbar controls [MFC], command ID
- menu items, associating with IDs
- user interface objects [MFC], associating with IDs
- command IDs, user interface objects
- command routing [MFC], MFC
- command handling [MFC], user-interface objects
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e085c6d9e4d030c8db44e11e570ffa1033abee35
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="user-interface-objects-and-command-ids"></a>Objetos de interfaz de usuario e identificadores de comando
Elementos de menú, botones de barra de herramientas y teclas de aceleración son "objetos de interfaz de usuario" capaces de generar comandos. Cada objeto de interfaz de usuario de este tipo tiene un identificador. Asociar un objeto de interfaz de usuario con un comando asignando el mismo identificador al objeto y el comando. Como se explica en [mensajes](../mfc/messages.md), se implementan como mensajes especiales. La ilustración "Comandos en el marco de trabajo" a continuación muestra cómo el marco de trabajo administra los comandos. Cuando un objeto de interfaz de usuario genera un comando, como `ID_EDIT_CLEAR_ALL`, uno de los objetos de la aplicación controla el comando, en la ilustración siguiente, el objeto de documento `OnEditClearAll` función se llama a través del mapa de mensajes del documento.  
  
 ![Comandos en el marco de trabajo](../mfc/media/vc385p1.gif "vc385p1")  
Comandos de Framework  
  
 La ilustración "Comando Actualizar en el marco de trabajo" muestra cómo MFC actualiza los objetos de interfaz de usuario, como elementos de menú y botones de barra de herramientas. Antes de desplegar un menú o durante el bucle de inactividad en el caso de los botones de barra de herramientas, MFC envía un comando de actualización. En la ilustración siguiente, llama a su controlador de comando de actualización, el objeto de documento `OnUpdateEditClearAll`, para habilitar o deshabilitar el objeto de interfaz de usuario.  
  
 ![Comando de actualización en el marco de trabajo](../mfc/media/vc385p2.png "vc385p2")  
Actualización de comandos de Framework  
  
## <a name="see-also"></a>Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)

