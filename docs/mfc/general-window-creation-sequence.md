---
title: "Secuencia de creaci&#243;n de ventanas general | Microsoft Docs"
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
  - "ventanas de marco [C++], crear"
  - "secuencia [C++]"
  - "secuencia [C++], creación de ventana"
  - "ventanas [C++], crear"
ms.assetid: 9cd8c7ea-5e24-429e-b6d9-d7b6041d8ba6
caps.latest.revision: 8
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Secuencia de creaci&#243;n de ventanas general
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se crea una ventana de propietario, como una ventana secundaria, el marco de trabajo usa mucho el mismo proceso que descrita en [Creación de documentos y vistas](../mfc/document-view-creation.md).  
  
 Todas las clases de ventana proporcionadas por MFC emplean [construcción de dos pasos](../mfc/one-stage-and-two-stage-construction-of-objects.md).  Es decir, durante una invocación de operador de C\+\+ **new** , el constructor asigna e inicializa un objeto DE c\+\+. pero no crea una ventana correspondiente de Windows.  Esto se hace después llamando a la función miembro de [crear](../Topic/CWnd::Create.md) de objeto de la ventana.  
  
 La función miembro de **crear** crea la ventana de Windows y almacena el `HWND` en el miembro de datos público [m\_hWnd](../Topic/CWnd::m_hWnd.md)de objeto de C\+\+.  **crear** proporciona flexibilidad completa sobre los parámetros de creación.  Antes de llamar a **crear**, quizás desee registrar una clase de ventana con la función global [Clase](../Topic/AfxRegisterWndClass.md) para establecer los estilos de icono y de clase del cuadro.  
  
 Para las ventanas de marco, puede utilizar la función miembro de [LoadFrame](../Topic/CFrameWnd::LoadFrame.md) en lugar de **crear**.  `LoadFrame` crea la ventana de Windows utilizando menos parámetros.  Obtiene muchos valores predeterminados de recursos, incluida la leyenda del cuadro, el icono, la tabla de aceleradores, y el menú.  
  
> [!NOTE]
>  El icono, la tabla de aceleradores, y recursos de menús deben tener un Id. de recurso común, como **IDR\_MAINFRAME**, para cargados por LoadFrame.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Objetos de la ventana](../mfc/window-objects.md)  
  
-   [Registrar la ventana “clase”](../mfc/registering-window-classes.md)  
  
-   [Objetos de destrucción de la ventana](../mfc/destroying-window-objects.md)  
  
-   [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)  
  
## Vea también  
 [Crear ventanas](../mfc/creating-windows.md)