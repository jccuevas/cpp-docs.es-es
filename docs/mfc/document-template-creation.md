---
title: "Clear plantillas de documentos | Microsoft Docs"
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
  - "constructores [C++], plantilla de documento"
  - "plantillas de documento"
  - "plantillas de documento, crear"
  - "MFC, plantillas de documento"
  - "plantillas, plantillas de documento"
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Clear plantillas de documentos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear un nuevo documento en respuesta a un comando de `New` o de **Abierta** de menú de **archivo** , plantilla de documento también crea una nueva ventana de marco a través de la que ver el documento.  
  
 El constructor de plantilla de documento especifica qué tipos de documentos, de ventanas, y vistas podrá la plantilla crear.  Esto viene determinada por los argumentos que se pasa al constructor de plantilla de documento.  El código siguiente se muestra la creación de [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para una aplicación de ejemplo:  
  
 [!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/CPP/document-template-creation_1.cpp)]  
  
 El puntero a un nuevo objeto de `CMultiDocTemplate` se utiliza como argumento a [AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md).  Los argumentos del constructor de `CMultiDocTemplate` incluyen el Id. de recurso asociado a los menús y los aceleradores de tipo de documento, y tres usos de la macro de [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) .  `RUNTIME_CLASS` devuelve el objeto de [Recursos](../mfc/reference/cruntimeclass-structure.md) para la clase de C\+\+ denominada como argumento.  Los tres objetos de `CRuntimeClass` pasados al constructor de plantilla de documento proporcionan la información necesaria para crear nuevos objetos de clases especificadas durante el proceso de creación de documentos.  El ejemplo muestra la creación de una plantilla de documento que cree objetos de `CScribDoc` con objetos de `CScribView` asociados.  Las vistas son enmarcadas por las ventanas secundarias estándar de marco MDI.  
  
## Vea también  
 [Plantillas de documento y el proceso de creación de documentos y vistas](../mfc/document-templates-and-the-document-view-creation-process.md)   
 [Crear documentos y vistas](../mfc/document-view-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)   
 [Crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)