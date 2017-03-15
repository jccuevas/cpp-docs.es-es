---
title: "Usar el editor de cuadros de di&#225;logo para agregar controles | Microsoft Docs"
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
  - "controles comunes [C++], agregar"
  - "controles [MFC], agregar a cuadros de diálogo"
  - "controles de cuadro de diálogo [C++], agregar a cuadros de diálogo"
  - "Editor de cuadros de diálogo, crear controles"
  - "controles comunes de Windows [C++], agregar"
ms.assetid: d3f9f994-7e54-4656-a545-42c204557c36
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar el editor de cuadros de di&#225;logo para agregar controles
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Al crear el recurso de la diálogo\- plantilla con [editor de cuadros de diálogo](../mfc/dialog-editor.md), debe arrastrar los controles de una tabla de los controles y los coloca en el cuadro de diálogo.  Esto agrega las especificaciones para ese control con el recurso de la diálogo\- plantilla.  Cuando se crea un objeto de diálogo y se llama a la función miembro de **crear** o de `DoModal` , el marco de trabajo crea un control y los lugares de Windows con en la ventana de cuadro de diálogo en la pantalla.  
  
 Puede en su lugar [crear controles a mano](../mfc/adding-controls-by-hand.md) si desea.  Es más trabajo.  
  
## Vea también  
 [Crear y usar controles](../mfc/making-and-using-controls.md)   
 [Controles](../mfc/controls-mfc.md)