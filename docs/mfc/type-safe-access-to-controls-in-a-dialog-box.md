---
title: "Acceso con seguridad de tipos a los controles en un cuadro de di&#225;logo | Microsoft Docs"
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
  - "controles comunes [C++], en cuadros de diálogo"
  - "controles [MFC], obtener acceso en cuadros de diálogo"
  - "cuadros de diálogo [C++], acceso con seguridad de tipos a los controles"
  - "cuadros de diálogo de MFC, acceso con seguridad de tipos a los controles"
  - "acceso con seguridad a los controles de cuadro de diálogo"
  - "acceso con seguridad de tipos a los controles de cuadro de diálogo"
  - "controles comunes de Windows [C++], en cuadros de diálogo"
ms.assetid: 67021025-dd93-4d6a-8bed-a1348fe50685
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Acceso con seguridad de tipos a los controles en un cuadro de di&#225;logo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los controles de un cuadro de diálogo puede usar las interfaces de las clases de control MFC, como por ejemplo `CListBox` y `CEdit`.  Puede crear un objeto de control y asociarlo a un cuadro de diálogo.  A continuación, puede obtener acceso al control a través de su interfaz de clase, llamando a las funciones miembro para operar en el control.  Los métodos aquí descritos están diseñados para proporcionarle acceso con seguridad de tipos a un control.  Esto es especialmente útil para controles como cuadros de edición y cuadros de lista.  
  
 Existen dos enfoques para llevar a cabo una asociación entre un control de un cuadro de diálogo y una variable de miembro de control de C\+\+ de una clase derivada de `CDialog`:  
  
-   [Sin asistentes para código](../mfc/type-safe-access-to-controls-without-code-wizards.md)  
  
-   [Con asistentes para código](../mfc/type-safe-access-to-controls-with-code-wizards.md)  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)