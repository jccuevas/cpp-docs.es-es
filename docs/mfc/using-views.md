---
title: "Usar vistas | Microsoft Docs"
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
  - "CView (clase), vista de arquitectura"
  - "dibujar, datos"
  - "interactuar con usuarios y rol de clase de vista"
  - "MFC, vistas"
  - "imprimir datos"
  - "representación de datos"
  - "datos proporcionados por el usuario, interpretar a través de una clase de vista"
  - "clases de vista, rol en mostrar los datos de aplicación"
  - "clases de vista, rol en administrar la interacción del usuario"
  - "vistas, utilizar"
ms.assetid: dc3de6ad-5c64-4317-8f10-8bdcc38cdbd5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Usar vistas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las responsabilidades de vista son mostrar los datos de documento gráficamente el usuario y aceptar e interpretar los datos proporcionados por el usuario como operaciones en el documento.  Las tareas de la escritura de la clase de vista son:  
  
-   Escriba la función miembro de [OnDraw](../Topic/CView::OnDraw.md) de la clase de vista, que presenta los datos del documento.  
  
-   Conectar los mensajes adecuados de Windows y los objetos de la interfaz de usuario como elementos de menú al miembro del controlador de mensajes funcionan en la clase de vista.  
  
-   Implemente los controladores para interpretar los datos proporcionados por el usuario.  
  
 Además, puede necesitar reemplazar otras funciones miembro de `CView` en la clase derivada de la vista.  En particular, puede que desee reemplazar [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) para realizar una inicialización especial para que la vista y [OnUpdate](../Topic/CView::OnUpdate.md) realicen ninguna procesamiento especial necesario justo antes que la vista se redibuja.  Para los documentos de varias páginas, también debe reemplazar [OnPreparePrinting](../Topic/CView::OnPreparePrinting.md) para inicializar el cuadro de diálogo imprimir con el número de páginas a imprimir y otra información.  Para obtener más información sobre reemplazar funciones miembro de `CView` , vea la clase [CView](../mfc/reference/cview-class.md) en *la referencia de MFC*.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Clases derivadas de vista disponible en MFC](../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [Dibujar en una vista](../mfc/drawing-in-a-view.md)  
  
-   [Interpretación de los datos proporcionados por el usuario con una vista](../mfc/interpreting-user-input-through-a-view.md)  
  
-   [La vista de impresión](../mfc/role-of-the-view-in-printing.md)  
  
-   [Vistas de desplazamiento y escala](../mfc/scrolling-and-scaling-views.md)  
  
-   [El inicializar y limpiar el documentos ni vistas](../mfc/initializing-and-cleaning-up-documents-and-views.md)  
  
## Vea también  
 [Arquitectura documento\/vista](../mfc/document-view-architecture.md)   
 [CFormView Class](../mfc/reference/cformview-class.md)   
 [Vistas de registros \(acceso a datos MFC\)](../data/record-views-mfc-data-access.md)   
 [Omitir el mecanismo de serialización](../mfc/bypassing-the-serialization-mechanism.md)