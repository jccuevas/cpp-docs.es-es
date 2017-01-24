---
title: "Controladores de mensajes | Microsoft Docs"
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
  - "control de comandos, controladores de mensajes"
  - "controladores"
  - "controladores, comando"
  - "controladores, message"
  - "controladores de mensajes"
  - "control de mensajes, funciones del controlador de mensajes"
ms.assetid: 51bc4e76-dbe3-4cc2-b026-3199d56b2fa9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controladores de mensajes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En MFC, una función dedicada *de controlador* procesa cada mensaje independiente.  Las funciones de controlador de mensajes son funciones miembro de una clase.  Esta documentación se usa *la función miembro de controladores de mensajes*de términos, *la función de controlador de mensajes*, *el controlador de mensajes*, y *el controlador* indistintamente.  Algunos tipos de controladores de mensajes también se denominan “controladores de comandos”.  
  
 La escritura de los controladores de mensajes explica una proporción alta de trabajo al escribir una aplicación de .NET framework.  Esta familia de caso describe cómo funciona el mecanismo de mensaje\- procesamiento.  
  
 ¿Qué el controlador para un mensaje hace?  Hace todo lo que desea hacer en respuesta a ese mensaje.  Puede crear controladores usando la ventana Propiedades de la clase, y después completa el código del controlador mediante el editor de código fuente.  
  
 Puede utilizar todas las funciones de Microsoft Visual C\+\+ y MFC para escribir controladores.  Para obtener una lista de todas las clases, vea [Información general de la biblioteca de clases](../mfc/class-library-overview.md) en *la referencia de MFC*.  
  
## Vea también  
 [Mensajes y comandos en el marco](../mfc/messages-and-commands-in-the-framework.md)