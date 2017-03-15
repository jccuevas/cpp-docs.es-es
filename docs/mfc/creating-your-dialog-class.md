---
title: "Creating Your Dialog (Clase) | Microsoft Docs"
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
  - "cuadros de diálogo [C++], crear"
  - "clases de cuadro de diálogo, Asistente para agregar clases"
  - "clases de cuadro de diálogo, crear"
  - "archivos [C++], crear"
  - "cuadros de diálogo de MFC, crear"
ms.assetid: d5321741-da41-47a8-bb1c-6a0e8b28c4c1
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Creating Your Dialog (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para cada cuadro de diálogo del programa, cree una nueva clase de diálogo para trabajar con el recurso de cuadro de diálogo.  
  
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md) explica cómo crear una nueva clase de diálogo.  Cuando se crea una clase de cuadro de diálogo con el asistente para la clase add, escriba los elementos siguientes en. H y archivos de .CPP especificado:  
  
 En. Archivo de h:  
  
-   Una declaración de la clase de diálogo.  La clase se deriva de [CDialog](../mfc/reference/cdialog-class.md).  
  
 En el archivo de .CPP:  
  
-   Un mapa de mensajes para la clase.  
  
-   Un constructor estándar para el cuadro de diálogo.  
  
-   Un reemplazo de la función miembro de [DoDataExchange](../Topic/CWnd::DoDataExchange.md) .  Modifique esta función.  Se utiliza el diálogo intercambio de datos y funciones de validación como se describe más adelante en [Diálogo de intercambio y validación](../mfc/dialog-data-exchange-and-validation.md).  
  
## Vea también  
 [Crear una clase de diálogo con los Asistentes para código](../mfc/creating-a-dialog-class-with-code-wizards.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)