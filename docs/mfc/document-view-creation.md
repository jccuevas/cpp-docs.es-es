---
title: "Crear documentos y vistas | Microsoft Docs"
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
  - "arquitectura documento/vista, crear documento/vista"
  - "documentos, crear"
  - "MFC, documentos"
  - "MFC, vistas"
  - "creadores de objetos"
  - "tablas [C++]"
  - "tablas [C++], objetos que crea cada objeto MFC"
  - "vistas, y ventanas de marco"
  - "vistas, crear"
ms.assetid: bda14f41-ed50-439d-af9e-591174e7dd64
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Crear documentos y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las implementaciones de las fuentes de los comandos de `New` y de **Abierta** \(entre otros\) en el menú de **archivo** .  La creación de un nuevo documento y su ventana asociada de la vista y el cuadro es un esfuerzo cooperativo entre el objeto application, una plantilla de documento, el documento recién creado, y la ventana creada recientemente del cuadro.  La tabla siguiente resume qué objetos crean a.  
  
### Creadores de objeto  
  
|Creator|Crea|  
|-------------|----------|  
|Application|Plantillas de documentos|  
|Plantillas de documentos|Documento|  
|Plantillas de documentos|Ventana frame|  
|Ventana frame|View|  
  
## Vea también  
 [Plantillas de documento y el proceso de creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Clear plantillas de documentos](../mfc/document-template-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)   
 [Crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)