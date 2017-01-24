---
title: "Acceso con seguridad de tipos a los controles sin Asistentes para c&#243;digo | Microsoft Docs"
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
  - "controles de cuadro de diálogo, obtener acceso"
  - "cuadros de diálogo, obtener acceso a controles"
ms.assetid: 325b4927-d49b-42b4-8e0b-fc84f31fb059
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Acceso con seguridad de tipos a los controles sin Asistentes para c&#243;digo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El primer enfoque para crear el acceso tipo\- seguro a los controles utiliza una función inline miembro para convertir el tipo de valor devuelto de la función miembro de `CWnd``GetDlgItem` de clase al tipo de control adecuado de C\+\+, como en este ejemplo:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#50](../mfc/codesnippet/CPP/type-safe-access-to-controls-without-code-wizards_1.cpp)]  
  
 Puede utilizar esta función miembro para obtener acceso al control de forma tipo\- segura con el código siguiente:  
  
 [!code-cpp[NVC_MFCControlLadenDialog#51](../mfc/codesnippet/CPP/type-safe-access-to-controls-without-code-wizards_2.cpp)]  
  
## Vea también  
 [Acceso con seguridad de tipos a los controles en un cuadro de diálogo](../mfc/type-safe-access-to-controls-in-a-dialog-box.md)   
 [Acceso con seguridad de tipos a los controles con Asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)