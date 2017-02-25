---
title: "Plantillas de documento y el proceso de creaci&#243;n de documentos y vistas | Microsoft Docs"
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
  - "CDocTemplate (clase)"
  - "plantillas de documento, y vistas"
  - "arquitectura documento/vista, crear documento/vista"
  - "iconos, de varias plantillas de documento"
  - "MFC, plantillas de documento"
  - "varias plantillas de documentos"
  - "plantilla de documento única"
  - "plantillas, plantillas de documento"
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Plantillas de documento y el proceso de creaci&#243;n de documentos y vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para administrar el proceso complejo de crear documentos con las vistas y ventanas asociadas de marco, el marco de trabajo usa dos clases de plantilla de documento: [CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) para aplicaciones SDI y [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) para las aplicaciones MDI.  `CSingleDocTemplate` puede crear y almacenar un documento de un tipo al mismo tiempo.  `CMultiDocTemplate` mantiene una lista de muchos documentos abiertos de tipos.  
  
 Algunas aplicaciones admiten tipos de documento.  Por ejemplo, una aplicación podría admitir documentos de texto y documentos de gráficos.  En una aplicación, cuando el usuario elige el comando New en el menú archivo, un cuadro de diálogo muestra una lista de nuevos tipos de documento posibles para abrir.  Para cada tipo de documento compatible, la aplicación utiliza un objeto distinto de plantilla de documento.  La ilustración siguiente muestra la configuración de una aplicación MDI que admite dos tipos de documento y mostrar varios documentos abiertos.  
  
 ![Aplicación MDI con dos tipos de documentos](../mfc/media/vc387h1.png "vc387H1")  
Una aplicación MDI con dos tipos de documentos  
  
 Las plantillas de documento se crean y mantenidas por el objeto application.  Una de las tareas clave realizadas durante la función de `InitInstance` de aplicación es crear una o más plantillas de documento de la clase correspondiente.  Esta característica se describe en [Creación de plantillas de documento](../mfc/document-template-creation.md).  El objeto application almacena un puntero a cada plantilla de documento en la plantilla de lista e proporciona una interfaz para agregar plantillas de documento.  
  
 Si necesita admitir dos o más tipos de documento, debe agregar una llamada adicional a [AddDocTemplate](../Topic/CWinApp::AddDocTemplate.md) para cada tipo de documento.  
  
 Un icono se registra para cada plantilla de documento basándose en su posición en la lista de plantillas de documento.  El orden de las plantillas de documento determina el orden que se agregan con llamadas a `AddDocTemplate`.  MFC supone que el primer recurso de icono de la aplicación es el icono de aplicación, el siguiente recurso de icono es el primer icono de documento, y así sucesivamente.  
  
 Por ejemplo, una plantilla de documento es el tercero de tres para la aplicación.  Si hay un recurso de icono de la aplicación en el índice 3, ese icono se utiliza para la plantilla de documento.  Si no, el icono en el índice 0 se utiliza como valor predeterminado.  
  
## Vea también  
 [Temas generales de MFC](../mfc/general-mfc-topics.md)   
 [Clear plantillas de documentos](../mfc/document-template-creation.md)   
 [Crear documentos y vistas](../mfc/document-view-creation.md)   
 [Relaciones entre objetos MFC](../mfc/relationships-among-mfc-objects.md)   
 [Crear nuevos documentos, ventanas y vistas](../mfc/creating-new-documents-windows-and-views.md)