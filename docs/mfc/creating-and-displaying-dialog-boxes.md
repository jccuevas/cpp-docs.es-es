---
title: "Crear y mostrar cuadros de di&#225;logo | Microsoft Docs"
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
  - "cuadros de diálogo de MFC, crear"
  - "cuadros de diálogo de MFC, mostrar"
  - "cuadros de diálogo modales, crear"
  - "cuadros de diálogo no modales, crear"
  - "abrir cuadros de diálogo"
ms.assetid: 1c5219ee-8b46-44bc-9708-83705d4f248b
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Crear y mostrar cuadros de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Crear un objeto de diálogo es una operación dos.  Primero, cree el objeto de diálogo, cree la ventana de cuadro de diálogo.  Cuadros de diálogo modales y no modales se diferencian en el proceso utilizado para crearlos y mostrar.  Las en la tabla siguiente se muestra cómo los cuadros de diálogo modales y no modales se construyen y se muestran normalmente.  
  
### Creación de diálogo  
  
|Tipo de diálogo|Cómo hacerlo|  
|---------------------|------------------|  
|[Modeless](../mfc/creating-modeless-dialog-boxes.md)|Construya `CDialog`, llame a la función miembro de **crear** .|  
|[Modal](../mfc/creating-modal-dialog-boxes.md)|Construya `CDialog`, llame a la función miembro de `DoModal` .|  
  
 Puede, si lo desea, crea el cuadro de diálogo de [plantilla de cuadro de diálogo de en\- memoria](../mfc/using-a-dialog-template-in-memory.md) que ha construido en lugar de un recurso de plantilla de cuadro de diálogo.  Éste es un tema avanzado, sin embargo.  
  
## Vea también  
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)