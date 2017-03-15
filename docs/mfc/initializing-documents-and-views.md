---
title: "Inicializar documentos y vistas | Microsoft Docs"
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
  - "documentos, inicializar"
  - "inicializar documentos"
  - "inicializar objetos, objetos de documentos"
  - "inicializar vistas"
  - "vistas, inicializar"
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Inicializar documentos y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los documentos se crean de dos maneras diferentes, por lo que la clase del documento debe admitir ambas maneras.  Primero, el usuario puede crear un nuevo, vacío documento con el comando del Archivo Nuevo.  En ese caso, inicialice el documento en el reemplazo de la función miembro de [OnNewDocument](../Topic/CDocument::OnNewDocument.md) de la clase [CDocument](../mfc/reference/cdocument-class.md).  En segundo lugar, el usuario puede utilizar el comando abierto en el menú archivo de crear un nuevo documento cuyo contenido se lean de un archivo.  En ese caso, inicialice el documento en el reemplazo de la función miembro de [OnOpenDocument](../Topic/CDocument::OnOpenDocument.md) de la clase **CDocument**.  Si ambas inicializaciones son iguales, puede llamar a un miembro común que la función de ambas invalidan, o `OnOpenDocument` puede llamar `OnNewDocument` para inicializar un documento limpio y a continuación finalizar la operación abierta.  
  
 Se crean vistas una vez creados los documentos.  El mejor momento para inicializar una vista es después de que el marco haya terminado de crear el documento, la ventana de marco, y.  Puede inicializar la vista reemplazando la función miembro de [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) de [CView](../mfc/reference/cview-class.md).  Si necesita reinicializar o ajustar algo cada vez el documento cambia, puede reemplazar [OnUpdate](../Topic/CView::OnUpdate.md).  
  
## Vea también  
 [Inicializar y limpiar documentos y vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)