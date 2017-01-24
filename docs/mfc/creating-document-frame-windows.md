---
title: "Crear ventanas de marco de documento | Microsoft Docs"
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
  - "ventanas de marco de documento, crear"
  - "plantillas de documento, y ventanas de marco de documento"
  - "ventanas de marco [C++], crear"
  - "MFC [C++], ventanas de marco"
  - "clase en tiempo de ejecución, y creación de ventana de marco de documento"
  - "tiempo de ejecución, información de clases"
  - "ventanas [C++], crear"
ms.assetid: 8671e239-b76f-4dea-afa8-7024e6e58ff5
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear ventanas de marco de documento
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[Creación de documentos y vistas](../mfc/document-view-creation.md) muestra cómo el objeto de [CDocTemplate](../mfc/reference/cdoctemplate-class.md) orquestra crear la ventana, el documento, y la vista y la conexión del cuadro de ellos todas juntas.  Tres argumentos de [Recursos](../mfc/reference/cruntimeclass-structure.md) al constructor de `CDocTemplate` especifican la ventana de marco, el documento, y las clases de vista que la plantilla de documento crea dinámicamente en respuesta a los comandos de usuario como el comando New en el menú archivo o el comando nueva ventana en un menú Ventana MDI.  Plantilla de documento almacena esta información para su uso posterior cuando crea una ventana de marco para una vista y un documento.  
  
 Para que el mecanismo de [RUNTIME\_CLASS](../Topic/RUNTIME_CLASS.md) funcione correctamente, las clases derivadas de la cuadro\- ventana deben declararse con la macro de [DECLARE\_DYNCREATE](../Topic/DECLARE_DYNCREATE.md) .  Esto es porque el marco necesita crear ventanas de marco de documento mediante el mecanismo dinámico de la construcción de la clase `CObject`.  
  
 Cuando el usuario elige un comando que cree un documento, el marco llama plantilla de documento para crear el objeto document, la vista, y la ventana de marco que mostrará la vista.  Cuando crea la ventana de marco de documento, la plantilla de documento crea un objeto de la clase adecuada \(una clase derivada de [CFrameWnd](../mfc/reference/cframewnd-class.md) para una aplicación SDI o de [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) para una aplicación MDI.  El marco de trabajo llama a la función miembro de [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) de objeto de la cuadro\- ventana para obtener información sobre la creación de recursos y crear la ventana de Windows.  El marco asocia el identificador de ventana al objeto de la cuadro\- ventana.  Se crea la vista como una ventana secundaria de la ventana de marco de documento.  
  
 Tenga cuidado sobre la decisión de [cuándo inicializar](../mfc/when-to-initialize-cwnd-objects.md)`CWnd`\- objeto derivado.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Derivando una clase de CObject \(el mecanismo dinámico de creación\)](../mfc/deriving-a-class-from-cobject.md)  
  
-   [Documento\/vista Creación \(plantillas y creación de la ventana de marco\)](../mfc/document-view-creation.md)  
  
-   [Ventanas de destrucción de cuadro](../mfc/destroying-frame-windows.md)  
  
## Vea también  
 [Usar ventanas de marco](../mfc/using-frame-windows.md)