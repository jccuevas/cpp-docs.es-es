---
title: "Controlar comandos en el documento | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "WM_COMMAND"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de comandos"
  - "control de comandos, comandos en documentos"
  - "documentos, controlar mensajes en"
  - "documentos, mapas de mensajes"
  - "control de mensajes, WM_COMMAND (mensajes)"
  - "mapas de mensajes, en clase de documento"
  - "WM_COMMAND"
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Controlar comandos en el documento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase de documento pueden controlar ciertos comandos generados por los elementos de menú, los botones de la barra de herramientas, o las teclas de aceleración.  De forma predeterminada, **CDocument** administra el Guardar y Guardar como comandos en el menú archivo, con la serialización.  Otros comandos que afectan a los datos también pueden ser controlados por las funciones miembro de documentos.  Por ejemplo, en el programa scribble, la clase `CScribDoc` proporciona un controlador para el comando desde la Borrar de edición, que elimina todos los datos almacenados actualmente en el documento.  Los documentos pueden tener mapas de mensajes pero, a diferencia de las vistas, documentos no pueden administrar mensajes estándar de Windows — sólo mensajes de **WM\_COMMAND** , o “comandos”.  
  
## Vea también  
 [Usar documentos](../mfc/using-documents.md)