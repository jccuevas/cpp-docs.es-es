---
title: "Cuadros de di&#225;logo modales y no modales | Microsoft Docs"
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
  - "cuadros de diálogo de MFC, modales"
  - "cuadros de diálogo de MFC, no modales"
  - "cuadros de diálogo modales"
  - "cuadros de diálogo no modales"
ms.assetid: e83df336-5994-4b8f-8233-7942f997315b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Cuadros de di&#225;logo modales y no modales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar la clase [CDialog](../mfc/reference/cdialog-class.md) para administrar dos clases de cuadros de diálogo:  
  
-   *Cuadros de diálogo modales*, que requieren que el usuario responder antes de continuar el programa  
  
-   *Los cuadros de diálogo*no modal, que permanecen en la pantalla y están disponibles para su uso en cualquier momento pero permiten otras actividades de usuario  
  
 La edición y procedimientos de recursos para crear una plantilla de diálogo son iguales en los cuadros de diálogo modales y no modales.  
  
 Crear un cuadro de diálogo para el programa requiere los pasos siguientes:  
  
1.  Utilice [editor de cuadros de diálogo](../mfc/dialog-editor.md) para diseñar el cuadro de diálogo y crear el recurso de la diálogo\- plantilla.  
  
2.  Cree una clase de diálogo.  
  
3.  Conectar [los controles de recurso dialog controladores de mensajes](../mfc/adding-event-handlers-for-dialog-box-controls.md) en la clase de diálogo.  
  
4.  Agregar los miembros de datos asociados a los controles de cuadro de diálogo y especificar [diálogo de intercambio de datos](../mfc/dialog-data-exchange.md) y [validaciones de datos de cuadro de diálogo](../mfc/dialog-data-validation.md) para los controles.  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)