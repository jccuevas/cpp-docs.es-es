---
title: 'Contenedores: Elementos de cliente | Documentos de Microsoft'
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
- OLE containers [MFC], client items
- client items and OLE containers
ms.assetid: 231528b5-0744-4f83-8897-083bf55ed087
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: aa80911ff14d329dc483cd6497393c6c5595ef2e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="containers-client-items"></a>Contenedores: Elementos de cliente
En este artículo se explica qué son los elementos de cliente y de qué clases debe derivar una aplicación sus elementos de cliente.  
  
 Elementos de cliente son elementos de datos que pertenecen a otra aplicación que están contenidos en o al que hace referencia el documento de una aplicación de contenedor OLE. Elementos de cliente cuyos datos se encuentran en el documento se incrustan; se vinculan los cuyos datos se almacenan en otra ubicación, al que hace referencia el documento contenedor.  
  
 La clase de documento en una aplicación OLE se deriva de la clase [COleDocument](../mfc/reference/coledocument-class.md) en lugar de en **CDocument**. El `COleDocument` clase hereda de **CDocument** toda la funcionalidad necesaria para utilizar la arquitectura documento/vista en qué MFC se basan las aplicaciones. `COleDocument`También define una interfaz que se trata de un documento como una colección de `CDocItem` objetos. Varios `COleDocument` se proporcionan funciones de miembro para agregar, recuperar y eliminar elementos de esa colección.  
  
 Cada aplicación contenedora debe derivar al menos una clase de `COleClientItem`. Objetos de esta clase representan elementos, incrustados o vinculados, en el documento OLE. Estos objetos existen mientras dura el documento que contiene, a menos que se eliminan del documento.  
  
 `CDocItem`es la clase base para `COleClientItem` y `COleServerItem`. Objetos de clases derivadas de estas dos actúan como intermediarios entre el elemento OLE y las aplicaciones cliente y servidor, respectivamente. Cada vez que se agrega un nuevo elemento OLE al documento, el marco de trabajo MFC agrega un nuevo objeto de la aplicación cliente `COleClientItem`-clase derivada a la colección del documento de `CDocItem` objetos.  
  
## <a name="see-also"></a>Vea también  
 [Contenedores](../mfc/containers.md)   
 [Contenedores: Archivos compuestos](../mfc/containers-compound-files.md)   
 [Contenedores: Problemas de la interfaz de usuario](../mfc/containers-user-interface-issues.md)   
 [Contenedores: Características avanzadas](../mfc/containers-advanced-features.md)   
 [Clase de COleClientItem](../mfc/reference/coleclientitem-class.md)   
 [COleServerItem (clase)](../mfc/reference/coleserveritem-class.md)
