---
title: "Ciclo de vida de un cuadro de di&#225;logo | Microsoft Docs"
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
  - "cuadros de diálogo, ciclo de vida"
  - "ciclo de vida de cuadros de diálogo"
  - "cuadros de diálogo de MFC, ciclo de vida"
  - "cuadros de diálogo modales, ciclo de vida"
  - "cuadros de diálogo no modales, ciclo de vida"
ms.assetid: e16fd78e-238d-4f31-8c9d-8564f3953bd9
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Ciclo de vida de un cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Durante el ciclo de vida de un cuadro de diálogo, el usuario invoca el cuadro de diálogo, normalmente dentro de un controlador de comandos que cree e inicialice el objeto cuadro de diálogo, el usuario interactúa con el cuadro de diálogo, y se cierra el cuadro de diálogo.  
  
 Para los cuadros de diálogo modales, el controlador recopila los datos escribió el usuario una vez que se cierra el cuadro de diálogo.  Dado que existe el objeto de diálogo después de que cierra la ventana del cuadro de diálogo, puede usar simplemente las variables miembro de la clase de diálogo para extraer los datos.  
  
 Para los cuadros de diálogo no modal, puede extraer a menudo los datos del objeto de diálogo mientras el cuadro de diálogo todavía está visible.  En algún momento, se destruye el objeto de diálogo; cuando ocurre esto depende del código.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Crear y mostrar cuadros de diálogo](../mfc/creating-and-displaying-dialog-boxes.md)  
  
-   [Crear cuadros de diálogo modales](../mfc/creating-modal-dialog-boxes.md)  
  
-   [Crear cuadros de diálogo no modal](../mfc/creating-modeless-dialog-boxes.md)  
  
-   [Mediante una plantilla de cuadro de diálogo en memoria](../mfc/using-a-dialog-template-in-memory.md)  
  
-   [Establecer el color de fondo del cuadro de diálogo](../mfc/setting-the-dialog-box’s-background-color.md)  
  
-   [Inicializar el cuadro de diálogo](../mfc/initializing-the-dialog-box.md)  
  
-   [Controlar mensajes de Windows en el cuadro de diálogo](../mfc/handling-windows-messages-in-your-dialog-box.md)  
  
-   [Recuperar datos de objeto del diálogo](../mfc/retrieving-data-from-the-dialog-object.md)  
  
-   [Cerrar el cuadro de diálogo](../mfc/closing-the-dialog-box.md)  
  
-   [Destrucción del cuadro de diálogo](../mfc/destroying-the-dialog-box.md)  
  
-   [Diálogo de intercambio de datos \(DDX\) y validación \(DDV\)](../mfc/dialog-data-exchange-and-validation.md)  
  
-   [Cuadros de diálogo de la hoja de propiedades](../mfc/property-sheets-and-property-pages-mfc.md)  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)