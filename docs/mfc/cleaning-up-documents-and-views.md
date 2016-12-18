---
title: "Limpiar documentos y vistas | Microsoft Docs"
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
  - "documentos, limpieza"
  - "documentos, cerrar"
  - "vistas, limpieza"
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Limpiar documentos y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se cierra un documento, el marco llama primero su función miembro de [DeleteContents](../Topic/CDocument::DeleteContents.md) .  Si se asignada cualquier memoria en la pila durante el curso de la operación de documento, `DeleteContents` es el mejor lugar para desasignarla.  
  
> [!NOTE]
>  No debe desasignar datos de documento en el destructor del documento.  En el caso de una aplicación SDI, el objeto document podría reutilizar.  
  
 Puede reemplazar el destructor de una vista para desasignar cualquier memoria que se afectara asignado en el montón.  
  
## Vea también  
 [Inicializar y limpiar documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)