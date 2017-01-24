---
title: "Componentes de cuadro de di&#225;logo en el marco | Microsoft Docs"
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
  - "clases de cuadro de diálogo, componentes de cuadro de diálogo"
  - "plantillas de cuadro de diálogo, marco de trabajo de MFC"
  - "cuadros de diálogo de MFC, acerca de los cuadros de diálogo de MFC"
  - "cuadros de diálogo de MFC, crear"
  - "cuadros de diálogo de MFC, recurso de cuadro de diálogo"
ms.assetid: 592db160-0a8a-49be-ac72-ead278aca53f
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Componentes de cuadro de di&#225;logo en el marco
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el marco de trabajo de MFC, un cuadro de diálogo tiene dos componentes:  
  
-   Un recurso de la diálogo\- plantilla que especifica la posición del cuadro de diálogo controles y.  
  
     El recurso de cuadro de diálogo almacena una plantilla de cuadro de diálogo de la que Windows crea la ventana cuadro de diálogo y la muestra.  La plantilla especifica las características del cuadro de diálogo, incluida su tamaño, ubicación, estilo, y los tipos y las posiciones de los controles del cuadro de diálogo.  Utilizará normalmente una plantilla de diálogo almacenada como recurso, pero también puede crear dispone de la plantilla en memoria.  
  
-   Una clase de cuadro de diálogo, derivada de [CDialog](../mfc/reference/cdialog-class.md), proporcionar una interfaz de programación para administrar el cuadro de diálogo.  
  
     Un cuadro de diálogo es una ventana y se asocia a una ventana de Windows cuando está visible.  Cuando se crea la ventana de cuadro de diálogo, utilice el recurso de la diálogo\- plantilla como plantilla para crear los controles de ventana secundaria para el cuadro de diálogo.  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)