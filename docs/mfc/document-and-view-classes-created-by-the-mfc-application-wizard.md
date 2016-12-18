---
title: "Clases de documentos y de vistas creadas por el Asistente para aplicaciones MFC | Microsoft Docs"
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
  - "asistentes para aplicaciones [C++], clases de documento/vista creadas"
  - "clases de documento"
  - "clases de documento, creadas mediante asistentes para aplicaciones"
  - "clases de vista, creadas mediante asistentes para aplicaciones"
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Clases de documentos y de vistas creadas por el Asistente para aplicaciones MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El asistente para aplicaciones MFC proporciona una ventaja en el desarrollo de software creando clases esquemáticas de documento y de vista para usted.  A continuación [comandos y mensajes a estas clases](../mfc/reference/mapping-messages-to-functions.md) y utilizar el editor de código fuente de Visual C\+\+ para escribir su funciones miembro.  
  
 La clase document creada por el asistente para aplicaciones MFC se deriva de la clase [CDocument](../mfc/reference/cdocument-class.md).  La clase de vista se deriva de [CView](../mfc/reference/cview-class.md).  Los nombres que el Asistente para aplicaciones proporciona estas clases y los archivos que los contienen se basan en el nombre de proyecto que se proporciona en el cuadro de diálogo Asistente para aplicaciones.  En el Asistente para aplicaciones, puede utilizar la página clases generadas de para modificar los nombres predeterminados.  
  
 Algunas aplicaciones pueden necesitar más de una clase de documento, la clase de vista, o la clase de la cuadro\- ventana.  Para obtener más información, vea [Tipos de documento, vistas, y cuadro varias Windows](../mfc/multiple-document-types-views-and-frame-windows.md).  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)