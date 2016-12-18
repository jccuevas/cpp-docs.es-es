---
title: "Objetos de interfaz de usuario e identificadores de comando | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de comandos, objetos de interfaz de usuario"
  - "identificadores de comando, objetos de interfaz de usuario"
  - "enrutamiento de comandos, MFC"
  - "métodos abreviados de teclado, asociar a identificadores"
  - "elementos de menú, asociar a identificadores"
  - "MFC, enrutamiento de comandos"
  - "controles de barra de herramientas [MFC], identificador de comando"
  - "objetos de interfaz de usuario, asociar a identificadores"
ms.assetid: 4ea19e9b-ed1e-452e-bd33-7f509107a45b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Objetos de interfaz de usuario e identificadores de comando
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los elementos de menú, los botones de la barra de herramientas, y las teclas de aceleración son “objetos de la interfaz de usuario” capaces de representar comandos.  Por cada objeto de la interfaz de usuario tiene un identificador  Asocia un objeto de la interfaz de usuario con un comando asignando el mismo identificador del objeto y el comando.  Como se explica en [Mensajes](../mfc/messages.md), implementan los comandos como mensajes especiales.  La figura “comandos en el marco” siguiente muestra cómo el marco administra comandos.  Cuando un objeto de la interfaz de usuario genera un comando, como `ID_EDIT_CLEAR_ALL`, uno de los objetos de la aplicación administra el comando \(en la ilustración siguiente, la función de `OnEditClearAll` de document se denomina mediante la asignación de mensajes del documento.  
  
 ![Comandos de Framework](../mfc/media/vc385p1.png "vc385P1")  
Comandos de Framework  
  
 La figura “comando que actualiza en el marco” siguiente muestra cómo MFC actualiza objetos de la interfaz de usuario como elementos de menú y botones de la barra de herramientas.  Antes de que un menú interrumpa siguiente, o durante el bucle inactivo en el caso de los botones de la barra de herramientas, MFC distribuye un comando.  En la ilustración siguiente, el objeto document llama al controlador de comandos de actualización, `OnUpdateEditClearAll`, para habilitar o deshabilitar el objeto de la interfaz de usuario.  
  
 ![Actualización de comandos de Framework](../mfc/media/vc385p2.png "vc385P2")  
Actualización de comandos de Framework  
  
## Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)