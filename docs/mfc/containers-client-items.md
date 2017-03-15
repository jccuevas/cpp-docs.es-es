---
title: "Contenedores: Elementos de cliente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "elementos de cliente y contenedores OLE"
  - "contenedores OLE, elementos de cliente"
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Contenedores: Elementos de cliente
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica qué son los elementos de cliente y de qué clases debe derivar la aplicación sus elementos de cliente.  
  
 Los elementos de cliente son elementos de datos que pertenecen a otra aplicación contenidos en o se hace referencia en el documento OLE de aplicación contenedora.  Se insertan los elementos de cliente cuyo datos se contiene dentro del documento; se vinculan los cuyo datos se almacena en otra ubicación hace referencia el documento contenedor.  
  
 La clase del documento en una aplicación OLE se deriva de la clase [COleDocument](../mfc/reference/coledocument-class.md) en lugar de **CDocument**.  La clase de `COleDocument` hereda de **CDocument** toda la funcionalidad necesaria para utilizar la arquitectura documento\/vista en la que se basan las aplicaciones MFC.  `COleDocument` también define una interfaz que trate un documento como una colección de objetos de `CDocItem` .  Varias funciones miembro de `COleDocument` se proporcionan para agregar, recuperar, y eliminar elementos de esa colección.  
  
 Cada aplicación contenedora debe derivar por lo menos un tipo de `COleClientItem`.  Los objetos de esta clase representan los elementos, insertamos o vinculados, en el documento OLE.  Estos objetos existen mientras dure el documento que los contiene, a menos que se eliminen del documento.  
  
 `CDocItem` es la clase base para `COleClientItem` y `COleServerItem`.  Los objetos de clases derivadas de estos dos actúan como intermediarios entre el elemento OLE y las aplicaciones cliente y servidor, respectivamente.  Cada vez que un nuevo elemento OLE se agrega al documento, el marco de trabajo de MFC agrega un nuevo objeto de `COleClientItem`de aplicaciones cliente \- clase derivada a la colección de objetos de `CDocItem` .  
  
## Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Archivos compuestos](../mfc/containers-compound-files.md)   
 [Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)   
 [Contenedores: Características avanzadas](../mfc/containers-advanced-features.md)   
 [COleClientItem Class](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem Class](../mfc/reference/coleserveritem-class.md)